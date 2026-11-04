# Microsoft Sentinel & Azure SOC Automation Lab

## Objective
This repository documents the setup and configuration of a cloud-based Security Information and Event Management (SIEM) environment using Microsoft Sentinel. The project demonstrates endpoint onboarding, advanced log collection, and Security Operations Center (SOC) automation for incident response.

## Environment Setup
The local lab environment consists of virtual machines hosted on VMware Workstation Pro:
*   **Windows Endpoint**: A Windows 10 x64 virtual machine named `WIN10-LAB-01` configured with 8GB of RAM and 4 CPU cores[cite: 11].
*   **Linux Endpoint**: An Ubuntu 22.04 LTS virtual machine configured with 6GB of RAM and 4 CPU cores[cite: 10].

## Endpoint Onboarding
To integrate the local VMs with Azure and Microsoft Sentinel, onboarding scripts were executed on the endpoints to install the necessary agents:
*   **Windows**: The `OnboardingScript.ps1` script initially failed due to local security policies, which was resolved by modifying the execution policy to `RemoteSigned` using the `Set-ExecutionPolicy` cmdlet[cite: 9].
*   **Linux**: The `OnboardingScript.sh` script was executed via bash to download and install the Azure Connected Machine agent (`azcmagent`)[cite: 8].

## Data Collection & Telemetry
A Data Collection Rule (DCR) named `DCR-Sentinel-LAB` was created to filter and stream telemetry from the endpoints to the Azure Log Analytics Workspace[cite: 6].
*   **Event Logs**: Custom XPath queries were configured to collect critical Windows Event Logs across the Application, System, and Security channels[cite: 6].
*   **PowerShell Logging**: The DCR specifically targets `Microsoft-Windows-PowerShell/Operational!*` logs to monitor command-line activity[cite: 6]. This successfully captured Script Block Logging (Event ID 4104) telemetry during testing when executing commands such as `Write-Output "Hello Script Block Logging 2"`[cite: 7].

## SOC Automation & Incident Response
To automate the incident response workflow and reduce alert fatigue, an Azure Logic App playbook named `SOC-Email-Alert` was created and deployed to the `Sentinel-HEU-lab` resource group[cite: 4].
*   **Trigger**: The playbook is designed to trigger automatically upon the creation of a new Microsoft Sentinel incident[cite: 2, 3].
*   **Logic**: The workflow utilizes a `For each` loop structure to extract specific alert details associated with the grouped incident[cite: 2].
*   **Action**: The automation concludes by utilizing an Office 365 connection to send a high-importance email to the SOC analyst (`ncheejheu559@gmail.com`) containing the Incident Title, Alert Description, and Alert Severity[cite: 2].
