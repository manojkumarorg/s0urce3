Certainly! **PostgresDB** is an open-source time series database (TSDB) developed by InfluxData.
- Operation monitoring
- Real-time analytics,IOT
**Grafana**, on the other hand, is an open-source dashboard tool that works with various data sources.
- Visualize data from PostgresDB and create a dashboard and charts
---

# Setting up Prometheus and Grafana on Proxmox LXCs

March 02, 2023

What I'm doing:

- Setting up three LXC containers in my Proxmox node.
    - Prometheus
    - prometheus-pve-exporter
    - Grafana.
- pve-exporter will pull data from the Proxmox server
- Prometheus will pull the data from the pve-exporter container
- Grafana will pull from the Prometheus container and display it nice and pretty.

I assume you're already wondering why I would use three separate containers when I could just do this on one or even two. There's a few reasons, but the main one is that I prefer to have a bunch of small containers each doing one thing rather than a few larger containers each doing several things. Personal preference, but it works for me 🤷‍♀️

---

The following instructions assume you already have a Proxmox server up and running and know how to create LXC containers.

All the containers created in these steps are created with the Ubuntu Server 22.04 image.

### Setting up the Prometheus container

2cpu, 2gb ram, 8gb storage. Calling this one 'prometheus'

> The steps in this section are taken directly from [samynitsche.de](https://samynitsche.de/3-monitoring-proxmox-with-prometheus-and-grafana)

#### Create a group/user

```
groupadd --system prometheus \useradd -s /sbin/nologin --system -g prometheus prometheus
```

#### Create directories

```
mkdir /var/lib/prometheus \for i in rules rules.d files_sd; do mkdir -p /etc/prometheus/${i}; done
```

#### Download/install Prometheus

```
mkdir -p /tmp/prometheus && cd /tmp/prometheus \curl -s https://api.github.com/repos/prometheus/prometheus/releases/latest \  | grep browser_download_url \  | grep linux-amd64 \  | cut -d '"' -f 4 \  | wget -qi -
```

#### Extract files and move to correct directory

```
tar xvf prometheus*.tar.gz \cd prometheus \mv prometheus promtool /usr/local/bin/ \mv prometheus.yml  /etc/prometheus/prometheus.yml \mv consoles/ console_libraries/ /etc/prometheus/
```

#### Create systemd config

```
cd /etc/systemd/system/ && touch prometheus.service
```

```
nano prometheus.service
```

Paste in the following and save

```
[Unit]Description=PrometheusDocumentation=https://prometheus.io/docs/introduction/overview/Wants=network-online.targetAfter=network-online.target [Service]Type=simpleUser=prometheusGroup=prometheusExecReload=/bin/kill -HUP $MAINPIDExecStart=/usr/local/bin/prometheus \  --config.file=/etc/prometheus/prometheus.yml \  --storage.tsdb.path=/var/lib/prometheus \  --web.console.templates=/etc/prometheus/consoles \  --web.console.libraries=/etc/prometheus/console_libraries \  --web.listen-address=0.0.0.0:9090 \  --web.external-url= SyslogIdentifier=prometheusRestart=always [Install]WantedBy=multi-user.target
```

#### Set permissions

```
for i in rules rules.d files_sd; do chown -R prometheus:prometheus /etc/prometheus/${i}; done
```

```
for i in rules rules.d files_sd; do chmod -R 775 /etc/prometheus/${i}; done
```

```
chown -R prometheus:prometheus /var/lib/prometheus/
```

#### Start Prometheus

```
systemctl daemon-reload 
```

```
systemctl start prometheus 
```

```
systemctl enable prometheus
```

You should now be able to go to `http://<container-ip>:9090` and see the Prometheus instance running

---

### Installing proxmox-pve-exporter

The following steps are a modified version of [this post](https://blog.zwindler.fr/2020/01/06/proxmox-ve-prometheus/).

#### Create a new container

1cpu, 1gb ram, 6gb storage. Calling it 'prom-export'

#### Install pip3

```
apt-get install python3-pip 
```

```
pip3 install prometheus-pve-exporter
```

#### Make directory for pve_exporter

```
mkdir -p /usr/share/pve_exporter/
```

#### Add Proxmox credentials

```
nano /usr/share/pve_exporter/pve_exporter.yml
```

Add the following, but change to your Proxmox info

```
default:    user: proxmox_pve_user@pve    password: secret_password    verify_ssl: false
```

Save and exit

#### Test that it works

```
/usr/local/bin/pve_exporter /usr/share/pve_exporter/pve_exporter.yml
```

After running that in the console you should see something like:

```
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead. * Running on http://:9221Press CTRL+C to quit
```

#### Create systemd script

```
nano /etc/systemd/system/pve_exporter.service
```

Add the following to the file:

```
[Unit]Description=Proxmox VE Prometheus ExporterAfter=network.targetWants=network.target [Service]Restart=on-failureWorkingDirectory=/usr/share/pve_exporterExecStart=/usr/local/bin/pve_exporter /usr/share/pve_exporter/pve_exporter.yml 9221 192.168.X.X [Install]WantedBy=multi-user.target
```

Replace the IP address in that script with the IP of **this** container

Save and exit

#### Start pve_exporter service

```
systemctl daemon-reload
```

```
systemctl enable pve_exporter
```

```
systemctl start pve_exporter
```

Check that it's running with:

```
systemctl status pve_exporter
```

### Back on the Prometheus container

#### Add the pve_exporter data to Prometheus

```
nano /etc/prometheus/prometheus.yml
```

Add another `job_name` after the line `- targets: ["localhost:9000"]`

```
  - job_name: 'proxmox'    metrics_path: '/pve'    params:        # This is the ip address of the proxmox server        target: ['192.168.X.X']    static_configs:      # This is the container running pve_exporter      - targets: ["192.168.X.X:9221"]
```

Save and exit

#### Restart Prometheus

```
systemctl restart prometheus
```

You should now be able to go to `http://<prometheus-container-ip>:9090/targets` and see two entries. The first one is there by default, it's the Prometheus container. The second one should be the Proxmox metrics.

---

### Setup Grafana

#### Make new container

2cpu, 2gb ram, 8gb storage. Calling it 'grafana'.

#### Setup apt for Grafana

```
apt-get install apt-transport-https software-properties-common wget
```

```
wget -q -O /usr/share/keyrings/grafana.key https://apt.grafana.com/gpg.key
```

```
echo "deb [signed-by=/usr/share/keyrings/grafana.key] https://apt.grafana.com stable main" | tee -a /etc/apt/sources.list.d/grafana.list
```

#### Install Grafana

```
apt-get update
```

```
apt-get install grafana-enterprise
```

#### Start Grafana

```
systemctl daemon-reload
```

```
systemctl enable grafana-server.service
```

```
systemctl start grafana-server
```

#### Check that it's running

```
systemctl status grafana-server
```

If everything looks good, you should be able to go to `http://<grafana-container-ip>:3000` and see the login screen

Login with username/password `admin` and create a new password.

### Configure Grafana with Prometheus

Once logged in to Grafana:

- Click the gear icon at the bottom left
- Click the "Add data source" button
- Select Prometheus
- In the URL field, add the Prometheus container's IP and port like: `http://192.168.X.X:9090`
- Click "Save and test"

### Set up the pve-exporter dashboard

- Click the Dashboards icon on the left menu and select `+ Import`
- In the textfield that says "Import via grafana.com" enter `10347` and click "Load"
- Select Prometheus as the data source and save

Now you should have all your Proxmox metrics in this Grafana dashboard.

There's a chance that some of the labels may be overlapping and look all messed up. If so, just click the dropdown arrow at the top of that section and click "Edit". Expand the "Options" accordion and change the textfield that says `{{name}}` to `{{id}}`.

Refs:

- [https://samynitsche.de/3-monitoring-proxmox-with-prometheus-and-grafana](https://samynitsche.de/3-monitoring-proxmox-with-prometheus-and-grafana)
- [https://blog.zwindler.fr/2020/01/06/proxmox-ve-prometheus/](https://blog.zwindler.fr/2020/01/06/proxmox-ve-prometheus/) (French)

---

