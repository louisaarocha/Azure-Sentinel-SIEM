# Azure-Sentinel-SIEM

---

## Project Summary 
- In this project, I demonstrated the setup of Azure Sentinel, a cloud-based Security Information and Event Management (SIEM) system, integrated with a live virtual machine functioning as a honeypot. This hands-on tutorial showcased real-time cyberattacks, specifically RDP Brute Force attacks, originating from various global locations.

## Project Overview 

This project sets up an Azure Virtual Machine (VM) as a honeypot to attract potential attackers. It leverages Azure services, including Log Analytics Workspace (LAW) and Azure Sentinel, for security log analysis and geolocation data visualization.

## Key Highlights 
- Configured Azure Virtual Machine (VM) in Azure, intentionally exposing it to the internet without firewalls to attract potential attackers.
- Established a Log Analytics Workspace in Azure to serve as a centralized log repository for ingesting VM security logs.
- Employed a custom PowerShell script to extract IP addresses from Windows logs and sent them to a third-party API for geolocation data retrieval, including latitude, longitude, state, and province.
- Deployed Azure Sentinel, Microsoft's native SIEM solution, within Azure, allowing visualization of attack data on a geographical map.
  
## Project Steps

### Setup

#### Step 1: Azure VM Honeypot

- Created an Azure Virtual Machine configured as a honeypot.
- Connected to Azure VM using Remote Desktop Connection
- Established an inbound firewall rule to allow all internet traffic, making the VM discoverable to potential attackers.

<br>
<p>
  <img src="https://imgur.com/l0Q1KhG.png" height="60%" width="60%" alt="Alt text" title="Firewall">
</p>
<br>

#### Step 2: Log Analytics Workspace (LAW)

- Created a Log Analytics Workspace (LAW) in Azure to store VM's Windows Event Logs.
- Note: LAW acts as a centralized storage location for log and telemetry data for analysis and monitoring.
- Note: Azure Sentinel (SIEM) will connect to LAW for geospatial data display.

#### Step 3: Analyzing Security Logs

- Connected to the Azure VM using Remote Desktop Connection.
- Note: Access Windows Event Viewer > Security Log and search for 'ID:4625' to identify login failures.

<br>
<p>
  <img src="https://imgur.com/juZZIfc.png" height="60%" width="60%" alt="Alt text" title="Security Log">
</p>
<br>

#### Step 4: IP Geolocation Integration

- Created an account to use IP Geolocation services.
- Personal API key used in PowerShell scripts to gather geospatial data of attackers.

<br>
<p>
  <img src="https://imgur.com/Ws7nWHQ.png" height="60%" width="60%" alt="Alt text" title="Firewall">
</p>
<br>

## Log Analysis

### Extracting and Ingesting Data

#### Step 1: Extract Failed Login Attempts

- Used PowerShell script with an API to extract failed login attempts from the Windows Security Event Log.
- Saved data to a custom log file on the Azure VM to capture geospatial data of attackers.

<br>
<p>
  <img src="https://imgur.com/Y55McxW.png" height="60%" width="60%" alt="Alt text" title="Firewall">
</p>
<br>

#### Step 2: Transfer Data to LAW - Extracting/Creating New Fields

- Accessed Azure Log Analytics Workspace (LAW) in the Azure Portal.
- Created a custom log to ingest data from the custom log file on the VM.
- Utilized Kusto Query Language (KQL) with regex patterns to extract specific fields from the raw data and created new fields based on the extracted values.

<br>
<p>
  <img src="https://imgur.com/Af5gahW.png" height="60%" width="60%" alt="Alt text" title="Firewall">
</p>
<br>

### Visualization

#### Step 3: Workbook Configuration in Azure Sentinel

- Set up a new workbook in Azure Sentinel and added LAW query.
- Configured map settings for geospatial data plotting.
- Displayed events on an interactive map.

<br>
<p>
  <img src="https://imgur.com/FOtLwWi.png" height="60%" width="60%" alt="Alt text" title="Map Set Up">
</p>
<br>

### Completion

#### Step 4: Project Completion

- Completed the project with an active map showing events plotted according to their geographic locations.

<br>
<p>
  <img src="https://imgur.com/vFUDVoZ.png" height="60%" width="60%" alt="Alt text" title="Map">
</p>
<br>

## 

### Utilities Used
- https://ipgeolocation.io/
  
### Languages Used
- PowerShell
- KQL
<br>

##

---

This project demonstrates the integration of Azure services for cybersecurity purposes, offering insights into threat detection and geospatial analysis.
