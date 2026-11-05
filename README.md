
# Nginx Web Server Deployment & Automated Log Analyzer

## Overview
A hands-on Linux systems administration and automation project showcasing web server deployment, service management, and CLI-based log parsing. This project demonstrates how to configure an Nginx HTTP server on Linux, troubleshoot real-world port binding and service conflicts, and write an automated Bash script using Unix text-processing utilities (`awk`, `sort`, `uniq`, `head`) to extract actionable security and performance metrics from server access logs.

---

## Core Features & System Capabilities
* **Nginx Web Server Deployment:** Configured an active Nginx HTTP server on port 80, resolving daemon binding conflicts with legacy Apache services.
* **Log Analysis Automation (`log_analyzer.sh`):** Developed a shell script to automate real-time log parsing from `/var/log/nginx/access.log`.
* **Traffic Insights:**
  * Identifies the **Top 5 Most Requested Endpoints** (URIs).
  * Tracks the **Top 5 Request Source IP Addresses**.
  * Generates an **HTTP Status Code Breakdown** (e.g., `200 OK`, `304 Not Modified`, `404 Not Found`).

---

## System Requirements & Prerequisites
* **OS:** Linux (Tested on Kali Linux / Debian-based distributions)
* **Web Server:** Nginx
* **Shell Environment:** Bash shell (`/bin/bash`)
* **Utilities:** `awk`, `sort`, `uniq`, `head`
* **Permissions:** `sudo` / root privileges (required to read system log files in `/var/log/nginx/`)

---

## Technical Troubleshooting & Key Learnings
During deployment, the web server initially encountered port binding conflicts and directory content overlaps. Key administrative steps taken include:
1. **Service Conflict Resolution:** Identified process conflicts on port 80 using `ss -lntp` and disabled conflicting Apache processes (`systemctl stop apache2`).
2. **Document Root Maintenance:** Cleaned up legacy web root overrides in `/var/www/html/` to ensure Nginx served the correct default index pages (`index.nginx-debian.html`).

---

How to Run the Log Analyzer
1. Clone the Repository
   git clone [https://github.com/YOUR-USERNAME/linux-projects.git]
   cd linux-projects/coding and screenshots/log analyzer nginx.txt
2. Make the Script Executable
   copy and paste the above script[log analyzer.txt in coding and screenshot folder] in nano editor
   chmod +x log_analyzer.sh
3. Generate Test Traffic (Optional)
   Run a few curl requests to generate active log data:
   curl http://localhost/
   curl http://localhost/about
   curl http://localhost/contact
   curl http://localhost/missing-page
4. Execute the Script
   Run the script with sudo permissions to read the access logs:
   sudo ./log_analyzer.sh
