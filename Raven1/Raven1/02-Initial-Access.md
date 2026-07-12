# 02 - Initial Access

## Objective

Obtain a shell on the target machine.

---

## Username Enumeration

Using WPScan, I discovered the following user.

```
michael
```

---

## Credential Discovery

After further enumeration, valid credentials were obtained.

*(Document the method you used here if you want.)*

---

## SSH Login

I connected to the target using SSH.

```bash
ssh steven@<TARGET_IP>
```

After authentication, I obtained a shell as the user **steven**.

---

## System Enumeration

To understand the environment, I executed:

```bash
whoami
hostname
id
pwd
```

---

## Flag 2

I searched the filesystem for flags.

```bash
find / -type f -iname "*flag*" 2>/dev/null
```

The second flag was located inside:

```
/var/www
```

### Screenshot
<img width="324" height="61" alt="image" src="https://github.com/user-attachments/assets/12c4e4d5-94a8-4b70-be58-efcb4a215439" />


---

## Summary

* Logged in through SSH.
* Obtained a shell as **steven**.
* Located the second flag inside `/var/www`.
