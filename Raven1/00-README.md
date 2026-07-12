# Raven 1 Walkthrough

A complete walkthrough of the **Raven 1** VulnHub machine covering reconnaissance, web enumeration, initial access, privilege escalation, and flag discovery.

> **Platform:** VulnHub
> **Difficulty:** Beginner – Intermediate
> **Operating System:** Linux

---

## Machine Overview

The Raven 1 machine focuses on:

* Network Enumeration
* Web Enumeration
* WordPress Enumeration
* Password Cracking
* Linux Enumeration
* MySQL Enumeration
* Privilege Escalation

---

## Walkthrough Structure

| Step                                                     | Description                                                         |
| -------------------------------------------------------- | ------------------------------------------------------------------- |
| [01-Enumeration.md](01-Enumeration.md)                   | Network and web enumeration using Nmap, Nikto, Gobuster, and WPScan |
| [02-Initial-Access.md](02-Initial-Access.md)             | Gaining initial access using Hydra and SSH                          |
| [03-Privilege-Escalation.md](03-Privilege-Escalation.md) | MySQL enumeration, John the Ripper, and privilege escalation        |
| [04-Flags.md](04-Flags.md)                               | Locations and discovery methods for all flags                       |
| [commands.md](commands.md)                               | Complete list of commands used during the assessment                |

---

## Attack Path

```text
Nmap
   │
   ▼
Nikto
   │
   ▼
WordPress (/wordpress)
   │
   ▼
WPScan
   │
   ▼
User: michael
   │
   ▼
Hydra
   │
   ▼
SSH Login (michael)
   │
   ▼
Flag 2 (/var/www)
   │
   ▼
Read wp-config.php
   │
   ▼
MySQL
   │
   ▼
wp_users
   │
   ▼
User: steven
Password Hash
   │
   ▼
John the Ripper
   │
   ▼
SSH Login (steven)
   │
   ▼
sudo -l
   │
   ▼
Python NOPASSWD
   │
   ▼
Root Shell
   │
   ▼
MySQL → wp_posts
   │
   ├── Flag 3
   └── Flag 4
```

---

## Tools Used

* Nmap
* Nikto
* Gobuster
* WPScan
* Hydra
* John the Ripper
* SSH
* MySQL
* Linux Command Line

---

## Skills Practiced

* Service Enumeration
* Directory Enumeration
* WordPress Enumeration
* Password Cracking
* Linux Enumeration
* Database Enumeration
* Privilege Escalation
* Root Access

---

## Flags Summary

| Flag   | Location                         |
| ------ | -------------------------------- |
| Flag 1 | Service Page Source Code         |
| Flag 2 | `/var/www`                       |
| Flag 3 | MySQL → `wordpress` → `wp_posts` |
| Flag 4 | MySQL → `wordpress` → `wp_posts` |

> **Note:** The actual flag values have been omitted from this repository. This walkthrough focuses on the methodology and techniques used to solve the machine.

---

## Screenshots

Store screenshots in the `images/` directory, for example:

```text
images/
├── nmap.png
├── nikto.png
├── wpscan.png
├── hydra.png
├── ssh-michael.png
├── mysql.png
├── john.png
├── ssh-steven.png
├── sudo-l.png
└── root.png
```

---

## Disclaimer

This repository is intended for educational purposes only. All testing was performed in a legal lab environment (VulnHub/TryHackMe). Do not attempt these techniques against systems without explicit authorization.

---

## Author

**Shlok Kaneriya**
* Learning: Cybersecurity | Penetration Testing | Linux | Web Security
