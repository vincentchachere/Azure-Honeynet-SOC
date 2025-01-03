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

<details>

<summary>

### 🎯 Part 1: Create the Resources

</summary>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/c40eeb3a-6612-4179-bf38-428ca0c8c033">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/16d7657b-79b4-4a0d-96fc-b6de19a6f066">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/dc8c3ee8-38ff-4333-bec7-97c9d337e35c">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/4a0a75b8-cc2b-4c8f-9149-2410e2a5bb1a">

</details>

<details>

<summary>

### 🎯 Part 2: Configure Network Security Group

</summary>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/a3710dbc-51ea-42dd-99af-d12295e35d10">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/60ada55d-bdf5-4987-96ec-06b0b95d8567">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/d15e4666-17fc-48fc-91a8-0b878ea4142c">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/6d7cbc7a-b32e-483f-aa27-6b404e41dd33">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/247c0106-4884-4df2-a843-6146613393fe">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/5bf17c39-4718-4503-8b6a-62262ba5e3ab">

</details>

<details>

<summary>

### 🎯 Part 3:

</summary>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/1555bb32-d1e8-4a5e-b0aa-bd01e60d3483">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/656ee0fb-8aa8-48c8-9576-4c768b77b810">

<br>
<br>
<br>

[SQL Server 2019 | Microsoft Evaluate Center](https://www.microsoft.com/en-us/evalcenter/download-sql-server-2019)

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/71f29cf0-3f20-48d5-9fcb-da93ee57b4e5">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/8f248f3c-81b9-45db-aeb4-153c5443d1b1">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/e941e1ed-b18f-4fb2-bb96-9ce7a35a8cd8">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/28e36d43-ecad-4ea2-96c3-30542b4377e7">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/692c581c-e416-476a-b695-fbde533d69f1">

<br>
<br>
<br>

[Microsoft SQL Server Management Studio (SSMS)](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms)

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/0cc5b46d-26d5-462d-b106-3e4709e28f4c">

<br>
<br>
<br>

[Write SQL Server Audit events to the Security log](https://learn.microsoft.com/en-us/sql/relational-databases/security/auditing/write-sql-server-audit-events-to-the-security-log?view=sql-server-ver16)

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/3b1ebd5c-c478-41e5-bcf8-3fc6aacd0131">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/9191fe32-6f7d-407c-adf6-d142eec3b234">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/adb22bcd-0762-43cb-9086-b71eae89b0bd">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/0304a63b-fd56-4dfc-846a-e445dc37d882">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/02fa2f7f-df85-4d29-8590-8e1afd978b5e">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/eece8a88-2e0b-49d5-879e-d61ae5a72328">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/c49c2692-c8ca-49c1-bf29-e861f0882833">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/8295f7a1-5941-43b6-8134-d1add81b9c86">

</details>

<details>

<summary>

### 🎯 Part 4:

</summary>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/8f84a869-0f4b-4086-92df-f67bd85ffc77">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/4a1841c7-66d7-498e-bd58-21f2e81f9048">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/0510951c-500a-4013-9547-3d3cd3748cab">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/3f151cbd-229e-417a-8138-7b4fa9610dce">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/facee424-f3bb-47c8-a379-679031d20fd1">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/1e9e53a9-9e47-4b3d-863c-0531e49c2787">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/1b45e566-81c5-412b-b01d-892cb317b066">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/5d593dee-da9a-4bcf-a706-18cfb3631a07">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/9d29e9aa-e1e8-4c8f-8a5b-6bf6c6bf370b">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/b3539d95-4ce0-4f22-8cb9-7e492ef6c150">

</details>

<details>

<summary>

### 🎯 Part 5:

</summary>

<br>
<br>
<br>

<img width="800" alt="isolated" src="">

<br>
<br>
<br>

<img width="800" alt="isolated" src="">

<br>
<br>
<br>

<img width="800" alt="isolated" src="">

</details>

<details>

<summary>

### 🎯 Part 6: Attack Maps Before Hardening / Security Controls

</summary>

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

</details>

<details>

<summary>

### 🎯 Part 7: Metrics After Hardening / Security Controls

</summary>

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

</details>

<h1 align="center">Conclusion</h1>

In this project, a mini honeynet was built in Microsoft Azure with log sources integrated into a Log Analytics workspace. Microsoft Sentinel was used to trigger alerts and generate incidents from the ingested logs. Metrics were measured in the insecure environment before applying security controls and then reassessed after implementing them. The results showed a significant reduction in security events and incidents, highlighting the effectiveness of the applied measures.

However, if the network resources had been heavily utilized by regular users, more security events and alerts might have been generated during the 24-hour period following the implementation of the security controls.
