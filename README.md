# Cybersecurity-HomeLab

**Overview**
------------

This Cybersecurity Home Lab project aims to create a comprehensive environment for learning and practicing various aspects of cybersecurity. The lab consists of multiple systems running different services and tools to simulate real-world scenarios and facilitate hands-on experiences. Here's an diagram of the components:
<p align="center">
<img src="Images/Network%20Diagram.png" alt="diagram" width="80%"/>
</p>
**Main System (Ubuntu Server):**

*   Samba Server: Provides network file sharing capabilities, allowing users to share files and resources across the network securely.
*   OpenVPN Server: Enables secure remote access to the lab environment, allowing users to connect to the network securely from outside locations.
*   DNS Server (Pi-hole): Runs as a Docker container and serves as a DNS sinkhole to block ads and unwanted content, enhancing network security and privacy.
*   DuckDNS Dynamic DNS Server: Also running as a Docker container, it provides dynamic DNS functionality, enabling easy access to lab services from outside the network.

**Domain Controller (Virtual Machine):**

*   Acts as a central authority for user authentication and resource management in a Windows-based network environment.
*   Allows practice with Active Directory services, user management, group policies, and other domain-related configurations.

**Windows Client (Virtual Machine):**

*   Provides a Windows-based operating system for testing and practicing various client-side attacks and security configurations.
*   Can be used to simulate real-world scenarios involving Windows systems.

**pfSense Next-Generation Firewall (Virtual Machine):**

*   Serves as a powerful network security appliance, providing advanced firewalling, routing, and VPN capabilities.
*   Allows the creation of network segments, firewall rules, and other security configurations.
*   Facilitates the practice of network security, intrusion detection, and prevention techniques.

**Elastic SIEM Solution:**

*   Elasticsearch, Logstash, and Kibana (ELK stack) are used to create a Security Information and Event Management (SIEM) system.
*   Collects, analyzes, and visualizes log data from various sources, enabling efficient threat detection and incident response.

**Vulnerable Machines (Docker Containers):**

*   Various intentionally vulnerable machines are set up as Docker containers to simulate real-world vulnerabilities and enable penetration testing and ethical hacking practices.
*   Allows users to practice identifying, exploiting, and securing vulnerabilities.

**Additional Docker Containers:**

*   Trilium Notes: A personal knowledge management tool for organizing notes, documents, and information securely.
*   Nextcloud: A self-hosted cloud storage and collaboration platform, providing secure file synchronization and sharing capabilities.
*   Jellyfin: A media server for organizing and streaming media files securely.
*   Webtop: A web-based desktop environment for remote access and management of the lab environment.

**Kali Linux (Attack Machine):**

*   Kali Linux is a specialized Linux distribution designed for advanced penetration testing and ethical hacking.
*   It serves as an attack machine within the lab, allowing users to perform security assessments, exploit vulnerabilities, and test various hacking techniques.

By setting up this comprehensive lab environment, users can gain hands-on experience in various areas of cybersecurity, including network security, system hardening, vulnerability assessment, penetration testing, incident response, and more. The lab provides a safe and controlled environment to practice and develop practical skills in a realistic context.
