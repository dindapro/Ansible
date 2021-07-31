# Selecting Hosts with Host Patterns

## list-hosts

```bash
[student@workstation projects-host]$ ansible db1.example.com -i inventory1 \
> --list-hosts
  hosts (1):
    db1.example.com
```

```bash
[student@workstation projects-host]$ ansible 172.25.252.44 -i inventory1 \
> --list-hosts
 hosts (1):
    172.25.252.44
```

## list-hosts
```bash
[student@workstation projects-host]$ ansible all -i inventory1 --list-hosts
  hosts (17):
    srv1.example.com
    srv2.example.com
    s1.lab.example.com
    s2.lab.example.com
    jupiter.lab.example.com
    saturn.example.com
    db1.example.com
    db2.example.com
    db3.example.com
    lb1.lab.example.com
    lb2.lab.example.com
    file1.lab.example.com
    web1.lab.example.com
    file2.example.com
    172.25.252.23
    172.25.252.44
    172.25.252.32
```

## with asterisk (*)

```bash

[student@workstation projects-host]$ ansible '*.example.com' -i inventory1 \
> --list-hosts
  hosts (14):
    jupiter.lab.example.com
    saturn.example.com
    db1.example.com
    db2.example.com
    db3.example.com
    lb1.lab.example.com
    lb2.lab.example.com
    file1.lab.example.com
    web1.lab.example.com
    file2.example.com
    srv1.example.com
    srv2.example.com
    s1.lab.example.com
    s2.lab.example.com
```

## Filtering host pattern
```bash
[student@workstation projects-host]$ ansible '*.example.com, !*.lab.example.com' \
> -i inventory1 --list-hosts
  hosts (7):
    saturn.example.com
    db1.example.com
    db2.example.com
    db3.example.com
    file2.example.com
    srv1.example.com
    srv2.example.com
```
### list 

```bash
[student@workstation projects-host]$ ansible \
> lb1.lab.example.com,s1.lab.example.com,db1.example.com -i inventory1 \
> --list-hosts
  hosts (3):
    lb1.lab.example.com
    s1.lab.example.com
    db1.example.com
```

### wildcard
```bash
[student@workstation projects-host]$ ansible '172.25.*' -i inventory1 --list-hosts
  hosts (3):
    172.25.252.23
    172.25.252.44
    172.25.252.32
```

### Start with S. include member of group start with S
```bash
[student@workstation projects-host]$ ansible 's*' -i inventory1 --list-hosts
  hosts (7):
    saturn.example.com
    srv1.example.com
    srv2.example.com
    s1.lab.example.com
    s2.lab.example.com
    file2.example.com
    db2.example.com
```

### advance

```bash
[student@workstation projects-host]$ ansible 'prod,172*,*lab*' -i inventory1 \
> --list-hosts
  hosts (11):
    lb2.lab.example.com
    db1.example.com
    jupiter.lab.example.com
    172.25.252.23
    172.25.252.44
    172.25.252.32
    lb1.lab.example.com
    file1.lab.example.com
    web1.lab.example.com
    s1.lab.example.com
    s2.lab.example.com
```

### advance

```bash 
[student@workstation projects-host]$ ansible 'db,&london' -i inventory1 \
> --list-hosts
  hosts (2):
    db2.example.com
    db3.example.com
```