# 04 - Flags

## Key 1

Location

```
/robots.txt
```

Content

```
073403c8a58a1f80d943455fb30724b9
```

Method

robots.txt enumeration

---

## Key 2

Location

```
/home/robot/key-2-of3.txt
```

Content

```
3c174d6e0c48f30d3e2a1c1f3b8e9c9b
```

Method

Filesystem enumeration via Meterpreter

---

## Key 3

Location

```
/root/key-3-of-3.txt
```

Content

```
04787ddef27c6dee1ee94a3c5d8f1c10
```

Method

Nmap SUID privilege escalation to root

---

## Summary

| Flag | Location | Method |
|------|----------|--------|
| Key 1 | /robots.txt | robots.txt enumeration |
| Key 2 | /home/robot/key-2-of3.txt | Filesystem enumeration |
| Key 3 | /root/key-3-of-3.txt | SUID nmap → root shell |
