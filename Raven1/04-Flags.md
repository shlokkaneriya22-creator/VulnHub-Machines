# 04 - Flags

## Flag 1

Location

```
Service Page Source
```

Method

View Source

---

## Flag 2

Location

```
/var/www
```

Method

Filesystem Enumeration

---

## Flag 3

Location

```
MySQL
wordpress
wp_posts
```

Method

```sql
SELECT * FROM wp_posts;
```

---

## Flag 4

Location

```
MySQL
wordpress
wp_posts
```

Method

```sql
SELECT * FROM wp_posts;
```

---

<img width="897" height="310" alt="image" src="https://github.com/user-attachments/assets/1f5c11d9-34cc-423b-9f64-04625774fac0" />

## Summary

| Flag | Location | Method |
|------|----------|--------|
| Flag 1 | Service Page Source | HTML Source Inspection |
| Flag 2 | /var/www | Filesystem Enumeration |
| Flag 3 | wp_posts | MySQL Enumeration |
| Flag 4 | wp_posts | MySQL Enumeration |
