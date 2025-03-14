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

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/a7c3076e-b07e-4ef4-b08b-b5872ec8795a">

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

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/e9b22a2f-f19e-4398-b54c-f1927b730fb2">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/5fe85286-66ea-439e-9584-2a2a3e4fc99f">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/7e1bd313-3660-4039-a192-74814b2f1452">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/7ed00101-498c-4657-ac9d-7c1218220dbb">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/72b78c3b-68bf-4b24-92fa-d69ecc8f8dbb">

<br>
<br>
<br>

Download this file onto your PC:

https://github.com/vincentchachere/Sentinel-Maps-JSON/blob/main/geoip-summarized.csv

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/cbfde80f-a718-4da9-9b2e-ffcb459dc27c">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/41e3fdb8-e551-439f-8298-bb5dacff3b21">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/42122113-a671-428d-9c79-e61dbd847ec2">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/28393730-688f-4923-b575-cbc6957777d6">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/deb006cb-d986-4217-b845-1e972e985c86">

</details>

<details>

<summary>

### 🎯 Part 6:

</summary>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/1e5cbea5-78b7-42f8-b600-be3e2fbbee77">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/6426fb28-b6a3-43c2-838e-d1d72addd573">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/167ff9a0-2e40-4d5c-bafd-85609f137f40">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/a5add3f9-3663-4e1c-8d50-edf6aef87b18">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/ef4360bc-df96-4366-8bb0-3c846ae75a57">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/f7c13791-db2b-4502-91d9-58b6af4a5b43">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/adc2f093-1177-4a55-b806-6945ec0a9b92">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/0bd1e53b-9c31-43e2-95cf-4134e44c3d48">

</details>

<details>

<summary>

### 🎯 Part 7:

</summary>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/26662dc0-efd4-4b81-a894-0ef8ba8bc28f">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/29aaa8eb-aae5-409f-98b2-f2b1be20206c">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/6acb70ca-6fee-4979-96fb-7a885b73aa69">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/3f7284d4-b487-4c6e-bb59-5978271c7afb">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/354d7dbe-0975-4e3c-bbce-d55fbbe8ccf6">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/016fd387-b694-4a26-be15-f19d4a17b46f">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/00cc313d-8e2f-4c16-898f-ab851c627475">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/aac514f6-ef76-491f-8275-a9cc4b960a73">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/567b6a86-7969-490a-8e95-520c3da41928">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/ed388ea0-5c1f-4385-9521-502cd1723803">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/bc1221be-cdb7-4bcf-9450-48b3c1b04a00">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/7b6a5ca4-0e64-4cdb-adbf-005ce7b625ba">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/dc452f09-a777-46e6-9360-db454ae9a3c6">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/f84f9f74-1c31-46e1-8e6c-ae965f834880">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/0ef126b6-d317-4909-999a-88ff82b7e41e">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/5aa139ce-e200-4970-8fe2-555175f99bc7">

</details>

<details>

<summary>

### 🎯 Part 8:

</summary>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/c4aab5c7-ffed-4c97-9bcf-85c3c564de4e">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/94e96200-f23c-4e5e-9ff1-da4a822a51e8">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/b6986ef8-6820-4124-bc0b-cd1a6c946bcd">

</details>

<details>

<summary>

### 🎯 Part 9:

</summary>

<img width="800" alt="isolated" src="">

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

### 🎯 Part 10: Attack Maps Before Hardening / Security Controls

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

### 🎯 Part 11: Metrics After Hardening / Security Controls

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
