A complete setup :
### Container Setup

Create a new Ubuntu LXC.

- Storage: 30 GB
- CPU: 2 Cores
- Memory: 4 GB
- Network: vmbr0 – Static IP: 10.80.80.60
- DNS: Host Settings

#### Update System

Start the machine and update the system:

```
apt update && apt upgrade -y
```

#### Install Dependencies

Run the following commands to install the dependencies for Wazuh:

```
apt install curl dnsutils net-tools sudo gnupg -y
```

#### Run Installation Script

Navigate to the tmp folder then download the script.

```
cd /tmp
curl -sO https://packages.wazuh.com/4.3/wazuh-install.sh
bash ./wazuh-install.sh -a
```

Once the installation is finished, you’ll receive the password to log in to the dashboard. But, we’re going to change the password before logging in. Alternatively, this password can be stored in a password manager instead of changing it.

![](https://wroberts.me/wp-content/uploads/2022/11/image-267.png)

#### Change Admin Password

Download the password change script:

```
curl -so wazuh-passwords-tool.sh https://packages.wazuh.com/4.3/wazuh-passwords-tool.sh
```

Then run the script with:

```
bash wazuh-passwords-tool.sh -u admin -p <newpassword>
```

The new password must meet complexity requirements so the script will throw an error if they are not met. After the script finishes running, clear the bash history.

```
history -c
```

Then, reboot the system.

## Configuring Wazuh

### Initial Setup

#### Configure Firewall Rules

If your firewall rules block traffic between the networks the Wazuh server sits on and the machines it monitors, make sure ports 1514 and 1515 are open.

![](https://wroberts.me/wp-content/uploads/2022/11/image-270-1024x344.png)

![](https://wroberts.me/wp-content/uploads/2022/11/image-270-1024x344.png)

#### Logging In

You’ll get a privacy error when first entering.  Hit “advanced” then proceed.

![](https://wroberts.me/wp-content/uploads/2022/11/image-268.png)

Log in with “admin” and the password made during installation.

![](https://wroberts.me/wp-content/uploads/2022/11/image-269.png)

#### Enable Vulnerability Detector

The first thing we’re going to do is set up the vulnerability detector for the machines we’re monitoring. On the home screen, click on the arrow next to “Wazuh” near the top-left corner. Click “Management” then “Configuration.”

![](https://wroberts.me/wp-content/uploads/2022/11/image-271.png)

On the next page, click “Edit Configuration” in the top-right corner.

![](https://wroberts.me/wp-content/uploads/2022/11/image-272-1024x84.png)

Scroll down until you find the vulnerability detector line. Change it to yes.

![](https://wroberts.me/wp-content/uploads/2022/11/image-273.png)

Enable detection for Ubuntu and Debian systems as well since those systems are on our networks.

![](https://wroberts.me/wp-content/uploads/2022/11/image-274.png)

Make sure the Windows OS vulnerabilities are enabled as well.

![](https://wroberts.me/wp-content/uploads/2022/11/image-275.png)

Make sure aggregating vulnerabilities is enabled.

![](https://wroberts.me/wp-content/uploads/2022/11/image-276.png)

After that is done, click “Restart Manager.”

#### Create Groups

Open the Wazuh menu. Click on “Managemen,” then “Groups.”

![](https://wroberts.me/wp-content/uploads/2022/11/image-277.png)

Click “Add New Group” and save. I’m creating groups for the Active Directory network and the LAN where the Kali machine sits.

![](https://wroberts.me/wp-content/uploads/2022/11/image-278.png)

### Deploy Agents

#### Windows System Agent

In order to monitor a system, an agent needs to be installed on it. We’ll start with a Windows system.  For Windows, we’re going to install the GUI agent.

Log on to one of the Windows VMs. Open the web browser and go to [https://www.documentation.wazuh.com](https://www.documentation.wazuh.com/). Then, click on installation guide. Scroll down to “Installing the Wazuh Agent” then click on the Windows icon.

![](https://wroberts.me/wp-content/uploads/2022/11/image-278.png)

Download the installer.

![](https://wroberts.me/wp-content/uploads/2022/11/image-279.png)

Run the file.

![](https://wroberts.me/wp-content/uploads/2022/11/image-280.png)

Check the box for “Run Agent Configuration Interface.”

![](https://wroberts.me/wp-content/uploads/2022/11/image-281.png)

Open the file explorer. Go to C:\Program Files (x86)\ossec-agent and open the win32ui.

![](https://wroberts.me/wp-content/uploads/2022/11/image-282.png)

Enter the IP address of the Wazuh server and save. Then click “Manage” and “Start.”

![](https://wroberts.me/wp-content/uploads/2022/11/image-283.png)

You can view the logs by clicking “View” then “View Logs.” Pin the agent to the taskbar for ease of access later.

![](https://wroberts.me/wp-content/uploads/2022/11/image-284.png)

![](https://wroberts.me/wp-content/uploads/2022/11/image-285.png)

Go back to the Wazuh dashboard. You should see a 1 under total agents and active agents. Open the “Agents” menu and click “Agents.”

![](https://wroberts.me/wp-content/uploads/2022/11/image-286.png)

![](https://wroberts.me/wp-content/uploads/2022/11/image-287.png)

We can see our Domain Controller is now connected.

![](https://wroberts.me/wp-content/uploads/2022/11/image-291-1024x282.png)

##### Testing Alerts

Let’s test a situation where someone is trying to log in to the admin account of the domain controller with random passwords. We want to see if Wazuh picks up the failed log in attempts.

Go back to the windows server. Log out and try to log in with an incorrect password a few times.

![](https://wroberts.me/wp-content/uploads/2022/11/image-295.png)

Then, go back to the Wazuh dashboard and click on the name of the Windows machine in the Agents list.

![](https://wroberts.me/wp-content/uploads/2022/11/image-288.png)

From the menu, select “Security Events.”

![](https://wroberts.me/wp-content/uploads/2022/11/image-289.png)

Scroll down and you should see the failed log  in attempts. Of course, password policies can be put in place to prevent brute-forcing passwords but this is just for demonstration. 

Next, we’ll deploy an agent on a Linux system.

![](https://wroberts.me/wp-content/uploads/2022/11/image-290-1024x458.png)

#### Linux Agent

Go back to the Agents menu.  Click on “Deploy New Agent.”

![](https://wroberts.me/wp-content/uploads/2022/11/image-292.png)

Choose the appropriate operating system. We’re going to deploy the agent to the Suricata server, so it’ll be Debian/Ubuntu. The architecture will be x86_64 (64-bit). The server address will be the Wazuh server address.

![](https://wroberts.me/wp-content/uploads/2022/11/image-293.png)

Copy the commands and run them in the target machine. 

![](https://wroberts.me/wp-content/uploads/2022/11/image-294-1024x44.png)

![](https://wroberts.me/wp-content/uploads/2022/11/image-296.png)

Back in the Wazuh dashboard, refresh the agents list and you should see the machine added to the list.

![](https://wroberts.me/wp-content/uploads/2022/11/image-296.png)

## Threat Detection and Active Response

### Detection

I’m going to attempt to ssh into the Suricata server with an incorrect username and password.

![](https://wroberts.me/wp-content/uploads/2022/11/image-297.png)

In the Wazuh dashboard, under the security events for the Suricata server, the event is recorded.

![](https://wroberts.me/wp-content/uploads/2022/11/image-298-1024x89.png)

Click on the alert to expand the menu. Click on “JSON” to see more information such as the source IP and the username attempted.

![](https://wroberts.me/wp-content/uploads/2022/11/image-299.png)

### Active Response

Next, we’re going to have Wazuh respond to this sort of attack by dropping the packets.

Make note of the rule ID for this alert which is 5710 in this case.

![](https://wroberts.me/wp-content/uploads/2022/11/image-300.png)

From the menu in the top-left, go to “Management” then “Configuration. Then click “Edit Configuration.”

![](https://wroberts.me/wp-content/uploads/2022/11/image-302.png)

Scroll down to the “Active-Response” section of the XML.

![](https://wroberts.me/wp-content/uploads/2022/11/image-301.png)

Scroll to the bottom of this section and add the following lines:

```
  <active-response>
    <command>firewall-drop</command>
    <location>localhost</location>
    <rules_id>5710</rules_id>
    <timeout>1000</timeout>
  </active-response>
```

When done, the XML should look like this:

![](https://wroberts.me/wp-content/uploads/2022/11/image-303.png)

Then save the configuration and restart the manager.

### Confirming Threat Mitigation

Attempt to ssh into the Suricata server again. After entering the password, the terminal should hang for a while. Then, the connection should time out. This indicates the packets were dropped altogether  by Wazuh. 

![](https://wroberts.me/wp-content/uploads/2022/11/image-304.png)

### Index Management

The final step for configuring Wazuh is index management. Without an index policy, Wazuh indices will continue to fill up disk space and eventually cause performance issues. 

#### Create New Policy

![](https://wroberts.me/wp-content/uploads/2022/11/image-306.png)

![](https://wroberts.me/wp-content/uploads/2022/11/image-305.png)

![](https://wroberts.me/wp-content/uploads/2022/11/image-305.png)

![](https://wroberts.me/wp-content/uploads/2022/11/image-307.png)

#### Add Delete State

Scroll to the bottom of the screen and click “Add State.” Click “Add Action” and choose “Delete” from the drop down menu. Then click “Add Action.” Then “Save State.”

![](https://wroberts.me/wp-content/uploads/2022/11/image-308-1024x460.png)

![](https://wroberts.me/wp-content/uploads/2022/11/image-309.png)

#### Edit Hot State

Expand the hot state menu, then click “Edit.”

![](https://wroberts.me/wp-content/uploads/2022/11/image-310-1024x326.png)

Click the pencil under “Actions” to edit the number of replicas. Change it to 1. Then click “Edit Action.”

![](https://wroberts.me/wp-content/uploads/2022/11/image-311.png)

Then under transitions, edit the minimum index age to how long you want to keep the files before they are sent to the cold state. I went with 14 days. Click “Edit Action” then “Update State.”

![](https://wroberts.me/wp-content/uploads/2022/11/image-312.png)

![](https://wroberts.me/wp-content/uploads/2022/11/image-314.png)

#### Edit Cold State

Finally, edit the cold state by first deleting the replicas action. Then, add the “Read-Only” action and click “Edit Action.”

![](https://wroberts.me/wp-content/uploads/2022/11/image-313.png)

![](https://wroberts.me/wp-content/uploads/2022/11/image-315.png)

Click “Add Transition” and change the minimum index age to a lower number of days if desired. Click “Update State.” Afterwards, click “Create” in the bottom right-hand corner.

![](https://wroberts.me/wp-content/uploads/2022/11/image-316.png)

#### Apply Policy to Indices

Before the policy can take affect, it first has to be applied to the indices. Go back to the “Index Management” menu and click “Indices.”

![](https://wroberts.me/wp-content/uploads/2022/11/image-317.png)

Check the boxes of the indices you want the policy management to apply to, then click “Apply Policy.”

![](https://wroberts.me/wp-content/uploads/2022/11/image-318-1024x418.png)

That it for this setup. You now have a SIEM to monitor your network. In a future post, we’ll set up the Suricata server to forward its logs to Wazuh so those alerts can be viewed in Wazuh as well.