# Cybersecurity Internship Task 1: Local Network Port Scanning

**Author**: Neel Bhatt  
**Date**: June 23, 2025  
**Repository**: Cybersecurity-Task1

## Objective
The objective of this task is to perform network reconnaissance by scanning my local network to identify open ports and understand the exposure of network services. This exercise enhances my skills in using cybersecurity tools and analyzing potential security risks, as part of my cybersecurity internship.

## Tools Used
- **Nmap**: An open-source network scanning tool used to discover devices, open ports, and services on the network. Pre-installed on Kali Linux.
- ![Screenshot 2025-06-23 164756](https://github.com/user-attachments/assets/d01b5811-d236-4714-9dd6-7004de51c9f5)

- **Wireshark** (Optional): A packet analyzer used to capture and inspect network traffic, providing deeper insights into scan activities. Pre-installed on Kali Linux.
- ![Screenshot 2025-06-23 164819](https://github.com/user-attachments/assets/45e45d19-2d50-4818-a5ba-0e4017a80039)


## Environment
- **Operating System**: Kali Linux (2025.2 or latest version)
- **Network**: Local home Wi-Fi network (scanned with explicit permission)
- **IP Range**: `192.168.0.0/24` (determined via `ifconfig` or `ip addr`)

## Steps Performed
1. **Verified Tool Installation**:
   - Confirmed Nmap and Wireshark were installed on Kali Linux using `nmap --version` and `wireshark --version`.
   - Both tools were pre-installed, requiring no additional setup.

2. **Identified Local Network Range**:
   - Used `ifconfig` to find my IP address (e.g., `192.168.0.122`) and subnet mask (`255.255.255.0`).
   - ![Screenshot 2025-06-23 151737](https://github.com/user-attachments/assets/90f2323b-1f61-4b09-ac6a-9fe11e1a09be)

   - Determined the network range as `192.168.0.0/24`, covering IPs from `192.168.1.0` to `192.168.1.255`.

3. **Executed TCP SYN Scan with Nmap**:
   - Ran the command: `sudo nmap -sS 192.168.1.0/24`.
   - ![Screenshot 2025-06-23 153157](https://github.com/user-attachments/assets/1343dd5c-04b4-4f32-b8ae-9badea9ddd2c)
   - The `-sS` flag performed a stealthy TCP SYN scan, sending SYN packets to detect open ports without completing TCP handshakes.
   - Saved results to text and HTML formats:
     - Text: `sudo nmap -sS 192.168.0.0/24 -oN scan_results.txt`
     - HTML: `sudo nmap -sS 192.168.0.0/24 -oX scan_results.xml && xsltproc scan_results.xml -o scan_results.html`
     - ![Screenshot 2025-06-23 153838](https://github.com/user-attachments/assets/830f02cf-ed4c-4d77-9e96-af318eeb69e1)
     - To view the scan_results.html file in a web browser using htmlpreview.github.io, follow these steps:-
       
4. **Analyzed Scan Results**:
   - Reviewed `scan_results.txt` to identify devices (IP addresses) and their open ports.
   - Documented findings in `analysis.txt`, including:
     - IP addresses (e.g., `192.168.1.1`, `192.168.1.10`).
     - Open ports and services (e.g., `80/tcp - http`, `443/tcp - https`, `22/tcp - ssh`).
     - Researched services using IANA port assignments and online resources.
     - Identified potential risks, such as insecure services (e.g., FTP on port 21) or misconfigured web servers.

5. **Captured Packets with Wireshark** (Optional):
   - Launched Wireshark: `sudo wireshark &`
   - Selected the active interface (`wlan0`) and started capturing packets.
   - ![Screenshot 2025-06-23 161452](https://github.com/user-attachments/assets/75bd78da-3334-4c24-a864-01434fb6a956)
   - Re-ran the Nmap scan to generate traffic: `sudo nmap -sS 192.168.1.0/24`.
   - Filtered for `tcp` packets to observe SYN and SYN-ACK exchanges.
   - Saved the capture as `scan_capture.pcapng`.
   - ![Screenshot 2025-06-23 161512](https://github.com/user-attachments/assets/f720d20c-160e-4d28-b6de-fd9a914fa193)
   - Summarized observations in `analysis.txt`, confirming active services (e.g., HTTP responses on port 80).

6. **Prepared Submission**:
   - Created a GitHub repository named `Cybersecurity-Task1`.
   - Uploaded files: `scan_results.txt`, `scan_results.html`, `analysis.txt`, `scan_capture.pcapng`, and this `README.md`.
   - Committed and pushed files to the repository using Git commands.
   - Submitted the repository URL via the internship’s submission link before the 10:00 PM deadline.

## Files Included
- **`scan_results.html`**: Nmap scan output in HTML format, for better readability.
- **`analysis.txt`**: Detailed analysis of scanned IPs, open ports, services, and identified security risks.
- **`scan_capture.pcapng`** (Optional): Wireshark packet capture file, showing network traffic during the Nmap scan.
- **`README.md`**: This file, documenting the task process and findings.

## Key Learnings
- **Port Scanning Fundamentals**: Mastered the use of Nmap to discover open ports and services, understanding TCP SYN scan mechanics.
- **Network Reconnaissance**: Gained insights into mapping network devices and identifying their roles via open ports.
- **Service Exposure Analysis**: Learned to research common services (e.g., HTTP, SSH, FTP) and assess their security implications.
- **Packet Analysis**: Explored Wireshark to visualize network traffic, confirming scan results and detecting active services.
- **Security Risk Identification**: Recognized risks from open ports, such as unauthorized access or exploitable services, and mitigation strategies (e.g., firewalls, service hardening).
- **Documentation and Organization**: Developed skills in documenting technical processes clearly and structuring a professional GitHub repository.

## Challenges and Resolutions
- **Challenge**: Initial Nmap scan returned no results.
  - **Resolution**: Verified network range using `ip addr` and ensured I was connected to the correct network.
- **Challenge**: Wireshark showed excessive traffic, making analysis difficult.
  - **Resolution**: Applied a `tcp` filter to focus on relevant SYN/SYN-ACK packets.

## Future Improvements
- Explore advanced Nmap options (e.g., `-sV` for service versioning, `-O` for OS detection) to gather more detailed information.
- Learn to automate scans using scripts (e.g., Bash or Python) for efficiency.
- Deepen Wireshark proficiency by mastering filters and analyzing specific protocols.

## Acknowledgments
- **Elevate Labs Cybersecurity Internship**: For providing this hands-on learning opportunity.
- **Nmap and Wireshark Communities**: For maintaining robust, free tools that empower cybersecurity learning.
- **Neel Bhatt**: For diligently completing this task and documenting the process.

This repository represents my work for Task 1, submitted as part of my cybersecurity internship. All scans were performed on my local network with explicit permission, adhering to ethical and legal guidelines.

**Neel Bhatt**  
Cybersecurity Enthusiast  
June 23, 2025
