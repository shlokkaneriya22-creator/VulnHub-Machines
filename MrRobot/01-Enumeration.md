# 01 - Enumeration

## Objective

Identify services running on the target and gather information before exploitation.

---

## Network Scan

Started with an Nmap scan to discover open ports and services.

```bash
nmap -sV -sC <TARGET_IP>
```

### Results

| Port | Service |
| ---- | ------- |
| 22   | SSH     |
| 80   | HTTP    |

The target runs an Apache web server and an SSH service on a VirtualBox VM.

---

## Web Enumeration

Visited the web server and found a fake web shell animation — purely cosmetic, commands did nothing useful.

Checked `robots.txt`:

```text
User-agent: *
fsocity.dic
key-1-of-3.txt
```

Two entries discovered: a dictionary file and the first key.

---

## Wordlist Analysis

Downloaded `fsocity.dic` and inspected it.

```bash
wget http://<TARGET_IP>/fsocity.dic
wc -l fsocity.dic         # 858,160 lines
sort fsocity.dic | uniq | wc -l  # 11,451 unique
```

Filtered duplicates to speed up future brute-forcing:

```bash
sort fsocity.dic | uniq > fsocity_filtered.dic
```

---

## Directory Enumeration

Used Dirbuster with the default wordlist.

```bash
dirbuster
```

Discovered `/wp-admin` — indicating a WordPress installation.

---

## WordPress Enumeration

Confirmed WordPress 5.4.2 via Wappalyzer. Ran WPScan:

```bash
wpscan --url http://<TARGET_IP> -e u
```

No vulnerable plugins or themes were found, but the WordPress login page was noted for later use.

---

## Key 1

Located in `robots.txt`:

### Location

```
http://<TARGET_IP>/key-1-of-3.txt
```

### Content

```
073403c8a58a1f80d943455fb30724b9
```

---

## Enumeration Summary

- Open ports: 22 (SSH), 80 (HTTP)
- WordPress 5.4.2 installation
- Wordlist `fsocity.dic` obtained and filtered
- Key 1 retrieved from `robots.txt`
