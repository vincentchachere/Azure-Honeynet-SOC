<h1 align="center">Building a SOC + Honeynet in Azure (Live Traffic)</h1>

![Cloud Honeynet / SOC](https://github.com/user-attachments/assets/d1219c94-ab97-404e-b402-a7ad6a7c4605)

<h1 align="center">Introduction</h1>

In this project, I built a mini honeynet in Azure, integrated log sources into a Log Analytics workspace, and utilized Microsoft Sentinel to create attack maps, trigger alerts, and generate incidents. Security metrics were measured in the insecure environment over 24 hours, followed by the application of security controls to harden it. Metrics were then measured for another 24 hours. The results are outlined below, focusing on the following metrics:

- SecurityEvent (Windows Event Logs)
- Syslog (Linux Event Logs)
- SecurityAlert (Log Analytics Alerts Triggered)
- SecurityIncident (Incidents created by Sentinel)
- AzureNetworkAnalytics_CL (Malicious Flows allowed into our honeynet)

## Architecture Before Hardening / Security Controls

![Architecture Diagram](https://github.com/user-attachments/assets/76c260ab-2af8-4714-8900-6cb80032724e)

## Architecture After Hardening / Security Controls

![Architecture Diagram](https://github.com/user-attachments/assets/c7cd93ca-2f1b-4ad2-b4d4-85a3f608ffd6)

The architecture of the mini honeynet in Azure consists of the following components:

- Virtual Network (VNet)
- Network Security Group (NSG)
- Virtual Machines (2 windows, 1 linux)
- Log Analytics Workspace
- Azure Key Vault
- Azure Storage Account
- Microsoft Sentinel

For the "BEFORE" metrics, all resources were initially deployed with public internet exposure. Virtual Machines had unrestricted Network Security Groups and open built-in firewalls, while other resources used public endpoints without Private Endpoints. 

For the "AFTER" metrics, Network Security Groups were hardened to block all traffic except from the admin workstation. Additionally, all resources were secured using built-in firewalls and Private Endpoints.

## Attack Maps Before Hardening / Security Controls
![NSG Allowed Inbound Malicious Flows](https://i.imgur.com/1qvswSX.png)<br>
![Linux Syslog Auth Failures](https://i.imgur.com/G1YgZt6.png)<br>
![Windows RDP/SMB Auth Failures](https://i.imgur.com/ESr9Dlv.png)<br>

## Metrics Before Hardening / Security Controls

The following table shows the metrics we measured in our insecure environment for 24 hours:
Start Time 2023-03-15 17:04:29
Stop Time 2023-03-16 17:04:29

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 19470
| Syslog                   | 3028
| SecurityAlert            | 10
| SecurityIncident         | 348
| AzureNetworkAnalytics_CL | 843

## Attack Maps Before Hardening / Security Controls

```All map queries actually returned no results due to no instances of malicious activity for the 24 hour period after hardening.```

## Metrics After Hardening / Security Controls

The following table shows the metrics we measured in our environment for another 24 hours, but after we have applied security controls:
Start Time 2023-03-18 15:37
Stop Time	2023-03-19 15:37

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 8778
| Syslog                   | 25
| SecurityAlert            | 0
| SecurityIncident         | 0
| AzureNetworkAnalytics_CL | 0

<h1 align="center">Conclusion</h1>

In this project, a mini honeynet was built in Microsoft Azure with log sources integrated into a Log Analytics workspace. Microsoft Sentinel was used to trigger alerts and generate incidents from the ingested logs. Metrics were measured in the insecure environment before applying security controls and then reassessed after implementing them. The results showed a significant reduction in security events and incidents, highlighting the effectiveness of the applied measures.

However, if the network resources had been heavily utilized by regular users, more security events and alerts might have been generated during the 24-hour period following the implementation of the security controls.
