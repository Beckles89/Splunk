# Splunk SIEM on VirtualBox – Installation & Usage Guide

## 📌 Project Overview

This project demonstrates how to install, configure, and use **Splunk SIEM** in a **VirtualBox** virtual machine for cybersecurity monitoring and threat detection. The purpose is to simulate a security information and event management (SIEM) environment for learning, testing, and hands-on experience in a contained lab setup.

Through this project, I learned how to:

* Set up virtualized security monitoring environments
* Install and configure Splunk SIEM
* Create and manage data inputs for log ingestion
* Build and interpret security dashboards
* Configure alerts and reports
* Perform basic threat hunting and analysis

---

## 🛠 Requirements

Before starting, ensure you have:

* **Host OS**: Windows, macOS, or Linux
* **VirtualBox**: Latest version ([Download VirtualBox](https://www.virtualbox.org/))
* **Splunk Enterprise (Free Trial)**: [Download here](https://www.splunk.com/en_us/download.html)
* **Virtual Machine Image**:

  * Ubuntu Server or Windows Server ISO
* Minimum **System Resources**:

  * 4 GB RAM (8 GB recommended)
  * 2+ CPU cores
  * 20 GB storage
* Stable internet connection

---

## 🔹 Step 1: Set Up VirtualBox VM

1. **Open VirtualBox** and click **New**.
2. Name the VM (e.g., `Splunk-SIEM`).
3. Choose **Linux → Ubuntu (64-bit)** or **Windows Server** depending on ISO.
4. Assign **4 GB RAM** and **2 CPUs**.
5. Create a virtual hard disk (20 GB or more).
6. Attach your OS ISO file in **Settings → Storage**.
7. Enable **Bridged Adapter** in **Network Settings** for VM to get a local IP.

---

## 🔹 Step 2: Install Operating System

* Boot the VM from the ISO.
* Follow OS installation steps.
* Update packages after installation:

  ```bash
  sudo apt update && sudo apt upgrade -y
  ```

---

## 🔹 Step 3: Install Splunk SIEM

### On Ubuntu/Debian:

1. Download Splunk Enterprise:

   ```bash
   wget -O splunk.deb 'https://download.splunk.com/products/splunk/releases/latest/linux/splunk_package.deb'
   ```
2. Install Splunk:

   ```bash
   sudo dpkg -i splunk.deb
   ```
3. Start Splunk:

   ```bash
   sudo /opt/splunk/bin/splunk start --accept-license
   ```
4. Create admin credentials.

---

## 🔹 Step 4: Access Splunk Web UI

* Open your host machine browser.
* Navigate to:

  ```
  http://<VM_IP>:8000
  ```
* Login with your Splunk credentials.

---

## 🔹 Step 5: Add Data Inputs

* Go to **Settings → Add Data**.
* Select **Upload Files**, **Monitor**, or **Forward**.
* Configure syslog, firewall logs, or sample security logs for analysis.

---

## 🔹 Step 6: Create Security Dashboards

* Navigate to **Search & Reporting**.
* Use SPL (Search Processing Language) queries:

  ```spl
  index=* sourcetype=syslog | stats count by host
  ```
* Save searches as **Dashboards** for visualization.

---

## 🔹 Step 7: Configure Alerts

* Create alerts for specific triggers (e.g., multiple failed logins).
* Example SPL:

  ```spl
  index=* sourcetype=auth "failed password" | stats count by user
  ```
* Set thresholds and choose notification methods (email, script).

---

## 🧠 Skills Learned

1. **Virtualization Skills**

   * Creating and configuring VirtualBox VMs
   * Managing virtual networking (bridged/NAT)

2. **SIEM Administration**

   * Installing and configuring Splunk SIEM
   * Setting up data inputs and monitoring sources

3. **Log Analysis**

   * Understanding log formats (syslog, Windows Event Logs)
   * Searching and filtering logs with SPL

4. **Security Monitoring**

   * Detecting suspicious activities
   * Creating actionable alerts and dashboards

5. **Networking Knowledge**

   * Understanding IP configuration in virtual environments
   * Analyzing network traffic logs

---

## 📂 Repository Structure

```
splunk-siem-virtualbox/
│── README.md             # Documentation
│── screenshots/          # Installation & dashboard images
│── splunk-queries/       # Useful SPL queries
│── sample-logs/          # Test log files
```

---

## 📸 Screenshots

<img width="2560" height="1528" alt="Screenshot 2025-07-10 185522" src="https://github.com/user-attachments/assets/575ecc16-91e6-4afe-86bc-7cbb2e8ed00d" />
<img width="2560" height="1528" alt="Screenshot 2025-07-10 185623" src="https://github.com/user-attachments/assets/4e9841ce-a254-48c6-b59b-4015f9a77203" />
<img width="2560" height="1528" alt="Screenshot 2025-07-10 185716" src="https://github.com/user-attachments/assets/7502d6f1-6ce0-498d-8416-9ccc69d1b8ae" />
<img width="2560" height="1528" alt="Screenshot 2025-07-10 185741" src="https://github.com/user-attachments/assets/2f8c3c4c-27aa-4a67-a8f3-36db6a827fda" />
<img width="2560" height="1528" alt="Screenshot 2025-07-10 185854" src="https://github.com/user-attachments/assets/3e3ada13-dde3-4f9f-a792-741599f44332" />
<img width="2560" height="1528" alt="Screenshot 2025-07-10 190021" src="https://github.com/user-attachments/assets/dc9d226b-9dd4-4dda-ad49-fff34906ac1f" />
<img width="2560" height="1528" alt="Screenshot 2025-07-30 143247" src="https://github.com/user-attachments/assets/26647898-2577-4ff2-9faa-fd369f895d67" />

---
