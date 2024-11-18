# Programming skills
# Incident handling and documentation
# Log analysis
# Threat hunting
# Network traffic analysis

# INCIDENT HANDLING
# Digital Forensics & Incident Response (DFIR) skills
# Cloud security expertise
# SIEM operations
# Hacking skills
# Thinking outside the box



Actions performed in system or Network

# Cyber Kill chain:
The cyber kill chain consists of seven (7) different stages, as depicted in the image below: ![Cyber Kill Chain](https://academy.hackthebox.com/storage/modules/148/Cyber_kill_chain.png)
RECON
- Passive Information : Gathering Information from online
- Active  Information : Gathering Information by tools

WEAPONIZE:
- Malware tool to be used for Initial Gaining Access

DELIVERY
- Payload to be delivered to the victim
- phishing emails

EXPLOITATION:
- Executing a Code on a target system to gain access control

INSTALLATION:
- Droppers: piece of code deliver to the system to install malware(emails, sea)
- Backdoors: It can be done by the on going gaining access to the system(during exploitation stage)
- Rootkits: Hide its presence on system and it can be implemented in the dropper stage or exploitation

COMMAND & CONTROL:
-  After gaining control of part of their target’s system or accounts, the attacker can now track, monitor and guide their deployed cyberweapons and tool stacks remotely.

ACTION:
 - It is the act of copying, moving, or moving confidential data to a controlled location after the data theft.

NIST (4 STAGES):
 ![Handling Process](https://academy.hackthebox.com/storage/modules/148/handling_process.png)

Incident handling:
- Investigation
- Recovering

PREPARATION STAGE(PART-1):
- JUMP BAG - Contains all tool(hardware & Software) 

PART-2:
- DMARC-Email protection against phishing tool.

DMARC or **Domain-based Message Authentication, Reporting & Conformance** is an email authentication standard that leverages SPF and DKIM while adding an extra layer of protection.

 **Endpoint Hardening (& EDR)**

LOLBins-Attacker use this to exploit the code to perform malicious activities
whitelisting-Only the approved set of application can be accessed

Network Protection:
BYOD-bring you own device(approved devices 802.1x)


# DETECTION AND ANALYSIS STAGE (PART-1):

Alert from tools like SIEM,IPS/IDS,FIREWALLS,EDR

INITIAL INVESTIGATION:

- Date/Time when the incident was reported. Additionally, who detected the incident and/or who reported it?
- How was the incident detected?
- What was the incident? Phishing? System unavailability? etc.
- Assemble a list of impacted systems (if relevant)
- Document who has accessed the impacted systems and what actions have been taken. Make a note of whether this is an ongoing incident or the suspicious activity has been stopped
- Physical location, operating systems, IP addresses and hostnames, system owner, system's purpose, current state of the system
- (If malware is involved) List of IP addresses, time and date of detection, type of malware, systems impacted, export of malicious files with forensic information on them (such as hashes, copies of the files, etc.). 


# Detection & Analysis Stage (Part 2):

## The Investigation

- Creation and usage of indicators of compromise (IOC)-(EVIDENCE THAT SUGGEST THAT  NETWROK HAS BEEN BREACHED/ATTACKED)
- Identification of new leads and impacted systems
- Data collection and analysis from the new leads and impacted systems

![[investigation_new.webp]]
KNOW YOU TOOLS-PSEexEC in this user credentails are cached on the remote machine.
# Containment, Eradication, & Recovery Stage

Containment-Prevent an incident spreading across the network
Eradication-Completely wipe out the threat from the network
Recovery-Brings system to the production environment

# Post-Incident Activity Stage

## Reporting

- What happened and when?
- Performance of the team dealing with the incident in regard to plans, playbooks, policies, and procedures
- Did the business provide the necessary information and respond promptly to aid in handling the incident in an efficient manner? What can be improved?
- What actions have been implemented to contain and eradicate the incident?
- What preventive measures should be put in place to prevent similar incidents in the future?
- What tools and resources are needed to detect and analyze similar incidents in the future.


# SIEM Definition & Fundamentals


Security Information and Event Management (SIEM)


It is an open-source collection of mainly three applications (Elasticsearch, Logstash, and Kibana) that work in harmony to offer users comprehensive search and visualization capabilities for real-time analysis and exploration of log file sources.

![The Elastic Stack](https://academy.hackthebox.com/storage/modules/211/elastic.png)


![The Elastic Stack](https://academy.hackthebox.com/storage/modules/211/elastic1.png)


`Elasticsearch` is a distributed and JSON-based search engine, designed with RESTful APIs
`Logstash` is responsible for collecting, transforming, and transporting log file records.
`Kibana` serves as the visualization tool for Elasticsearch documents

Kibana Query Language (KQL) is a powerful and user-friendly query language designed specifically for searching and analyzing data in Kibana.

KQL :
Field:value pairs
 With the help of these you can able to identify the incident which it was performed in machine.
 [Windows Security Log Encyclopedia (ultimatewindowssecurity.com)](https://www.ultimatewindowssecurity.com/securitylog/encyclopedia/default.aspx)


The KQL query `event.code:4625` filters data in Kibana to show events that have the [Windows event code 4625](https://www.ultimatewindowssecurity.com/securitylog/encyclopedia/event.aspx?eventid=4625).

This type of query can help identify brute force attacks, password guessing, and other suspicious activities related to login attempts on Windows systems.

 KQL supports logical operators AND, OR, and NOT

```shell-session
event.code:4625 AND winlog.event_data.SubStatus:0xC0000072
```

 SubStatus value of 0xC0000072. {LOGIN FAILURE}
```shell-session
event.code:4625 AND winlog.event_data.SubStatus:0xC0000072 AND @timestamp >= "2023-03-03T00:00:00.000Z" AND @timestamp <= "2023-03-06T23:59:59.999Z"
```

Possible solutions:

-  Security Information and Event Management (SIEM) systems,
- Intrusion Detection and Prevention Systems (IDS/IPS)
- Endpoint Detection and Response (EDR) tools

Task:
detect, assess, respond to, report on, and prevent cybersecurity incidents.

# ROLES


| **Role**                        | **Responsibilities**                                                         |
|---------------------------------|-------------------------------------------------------------------------------|
| **SOC Director**                | Management, strategic planning, budgeting, staffing, alignment with objectives. |
| **SOC Manager**                 | Oversees daily operations, manages team, coordinates incident response.         |
| **Tier 1 Analyst**              | Monitors alerts, triages incidents, escalates to higher tiers.                 |
| **Tier 2 Analyst**              | In-depth analysis of incidents, identifies trends, develops mitigation strategies. |
| **Tier 3 Analyst**              | Handles complex incidents, threat hunting, enhances security posture.          |
| **Detection Engineer**          | Develops detection rules, implements and maintains monitoring tools.           |
| **Incident Responder**          | Manages active incidents, conducts forensics, containment, and remediation.    |
| **Threat Intelligence Analyst** | Gathers and analyzes threat intelligence, helps defend against emerging threats. |
| **Security Engineer**           | Develops, deploys, and maintains security tools and infrastructure.            |
| **Compliance & Governance Specialist** | Ensures adherence to standards, regulations, and best practices.       |
| **Security Awareness & Training Coordinator** | Develops and implements security training and awareness programs. |

# MITRE ATT&CK & Security Operations










Standard operating procedures:
When creating an SOP and documenting alert handling, consider the following:

- process.name
- process.parent.name
- event.action
- machine where the alert was detected
- user associated with the machine
- user activity within +/- 2 days of the alert's generation
- After gathering this information, defenders should engage with the user and examine the user's machine to analyze system logs, antivirus logs, and proxy logs from the SIEM for full visibility.

The SOC team should document all the above points, along with the Incident Response Plan, so that Incident Handlers can reference them during analysis

 Defenders will need to focus on event.action, IP address, and the reputation of the IP, among other factors
 
 In Windows we gonna notice these steps:
 
 **A filter option that allows us to filter the data before creating a graph. For example, if our goal is to display failed logon attempts, we can use a filter to only consider event IDs that match `4625 – Failed logon attempt on a Windows system`.**

**Do Not Monitor Computer Accounts**:

- **Explanation**: Computer accounts (which might appear in logs similar to user accounts but represent machines rather than human users) should not be included in monitoring, as this might lead to irrelevant data cluttering the visualization.

![[Pasted image 20240825014002.png]]

FOR DISABLED USERS(FAILED LOGIN ATTEMPTS):
![[Pasted image 20240825015827.png]]
 #  For RDP Logon related: 

 `4624 – An account was successfully logged on`
 
 Service account credentials are never used for RDP logons in corporate/real-world environments. We have been informed by the IT Operations department that all service accounts on the environment start with `svc-`.
 
 # SIEM Visualization Example 4: Users Added Or Removed From A Local Group (Within A Specific Timeframe)

- [4732: A member was added to a security-enabled local group](https://www.ultimatewindowssecurity.com/securitylog/encyclopedia/event.aspx?eventid=4732)
- [4733: A member was removed from a security-enabled local group](https://www.ultimatewindowssecurity.com/securitylog/encyclopedia/event.aspx?eventid=4733)



# WINDOWS EVENT LOGS

Each entry in the Windows Event Log is an "Event" and contains the following primary components:

1. `Log Name`: The name of the event log (e.g., Application, System, Security, etc.).
2. `Source`: The software that logged the event.
3. `Event ID`: A unique identifier for the event.
4. `Task Category`: This often contains a value or name that can help us understand the purpose or use of the event.
5. `Level`: The severity of the event (Information, Warning, Error, Critical, and Verbose).
6. `Keywords`: Keywords are flags that allow us to categorize events in ways beyond the other classification options. These are generally broad categories, such as "Audit Success" or "Audit Failure" in the Security log.
7. `User`: The user account that was logged on when the event occurred.
8. `OpCode`: This field can identify the specific operation that the event reports.
9. `Logged`: The date and time when the event was logged.
10. `Computer`: The name of the computer where the event occurred.
11. `XML Data`: All the above information is also included in an XML format along with additional event data.

`Application` logs:
information and error.

Information events provide general usage details about the application, such as its start or stop events. Conversely, error events highlight specific errors and often offer detailed insights into the encountered issues.


Windows logs:
```
[Event ID 1074](https://serverfault.com/questions/885601/windows-event-codes-for-startup-shutdown-lock-unlock) `(System Shutdown/Restart)`
```

```
[Event ID 6005](https://superuser.com/questions/1137371/how-to-find-out-if-windows-was-running-at-a-given-time) `(The Event log service was started)`:
```

```
[Event ID 6006](https://learn.microsoft.com/en-us/answers/questions/235563/server-issue) `(The Event log service was stopped)`
```

```
[Event ID 6013](https://serverfault.com/questions/885601/windows-event-codes-for-startup-shutdown-lock-unlock) `(Windows uptime)`
```

```
[Event ID 7040](https://www.slideshare.net/Hackerhurricane/finding-attacks-with-these-6-events) `(Service status change)`
```
