# 01 - Enumeration

## Objective

The first step was to identify the services running on the target machine and gather as much information as possible before attempting exploitation.

---

## Network Scan

I started by performing an Nmap scan.

```bash
nmap -sC -sV -A <TARGET_IP>
```

### Results

| Port | Service |
| ---- | ------- |
| 22   | SSH     |
| 80   | HTTP    |

The scan confirmed that the target was hosting an SSH service and a web server.

---

## Web Enumeration

I used Nikto to identify interesting files and directories.

```bash
nikto -h http://<TARGET_IP>
```

Nikto discovered a WordPress installation.

```
/wordpress
```

---

## Directory Enumeration

I used Gobuster to discover hidden directories.

```bash
gobuster dir -u http://<TARGET_IP> \
-w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
```

This confirmed several accessible directories including the WordPress installation.

---

## WordPress Enumeration

Using WPScan, I enumerated WordPress users.

```bash
wpscan --url http://<TARGET_IP>/wordpress -e u
```

The scan identified the username:

```
michael
```

---

## Flag 1

While exploring the website, I viewed the source code of the **Service** page.

The first flag was hidden inside the HTML source.

### Location

```
Service Page → View Source
```

### Screenshot
<img width="731" height="268" alt="image" src="https://github.com/user-attachments/assets/a068b0a9-9fdc-4b6b-a3ff-598b47ba59e6" />

---

## Enumeration Summary

* Identified SSH and HTTP services.
* Discovered WordPress.
* Enumerated the username **michael**.
* Located the first flag in the Service page source code.
