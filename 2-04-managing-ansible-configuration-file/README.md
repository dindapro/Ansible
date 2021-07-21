# deploy-manage

## prepare directory and file

### prepare folder
```bash
[teguh@redhat1 ~]$ mkdir deploy-manage
[teguh@redhat1 ~]$ cd deploy-manage/
[teguh@redhat1 deploy-manage]$

```

### create ansible.cfg

create ansible.cfg
```bash
[teguh@redhat1 deploy-manage]$ vi ansible.cfg

```

ansible.cfg
```
[defaults]
inventory = ./inventory
```
create inventory
```bash
[teguh@redhat1 deploy-manage]$ vi inventory
```

inventory file
```
[myself]
redhat1.mshome.net
[frontend]
redhat2.mshome.net
[backend]
redhat3.mshome.net
[app:children]
frontend
backend
```

## Without privilege escalation

```bash
[teguh@redhat1 deploy-manage]$ ansible app -i inventory --list-hosts
  hosts (2):
    redhat2.mshome.net
    redhat3.mshome.net
```

## With privilege escalation 
edit ansible.cfg
```bash
[defaults]
inventory = ./inventory

[privilege_escalation]
become = true
become_method = sudo
become_user = root
become_ask_pass = true
```

Test --list-hosts
```bash
[teguh@redhat1 deploy-manage]$ ansible app -i inventory --list-hosts
BECOME password: teguh
  hosts (2):
    redhat2.mshome.net
    redhat3.mshome.net

```