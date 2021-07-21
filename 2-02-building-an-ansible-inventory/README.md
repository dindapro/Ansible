# deploy-inventory

Edit /etc/ansible/hosts
```bash
[teguh@redhat1 ~]$ sudo vi /etc/ansible/hosts

[client]
172.27.88.52
```

check --list-hosts command
```bash
[teguh@redhat1 ~]$ ansible all --list-hosts
  hosts (1):
    172.27.88.52
```

check also --list-hosts ungrouped and client group
```bash
[teguh@redhat1 ~]$ ansible ungrouped --list-hosts
[WARNING]: No hosts matched, nothing to do
  hosts (0):

[teguh@redhat1 ~]$ ansible client --list-hosts
  hosts (1):
    172.27.88.52
```

create deploy-inventory directory on user home 
```bash
[teguh@redhat1 ~]$ mkdir ~/deploy-inventory
[teguh@redhat1 ~]$ cd deploy-inventory/
```

create inventory file 
```bash
[teguh@redhat1 deploy-inventory]$ vi inventory
```

inventory file
```bash
redhat1.mshome.net
[frontend]
redhat2.mshome.net
[backend]
redhat3.mshome.net
[app:children]
frontend
backend

```

check list all with new inventory file
```bash
[teguh@redhat1 deploy-inventory]$ ansible all -i inventory --list-hosts
  hosts (3):
    redhat1.mshome.net
    redhat2.mshome.net
    redhat3.mshome.net

```
check group and ungroup 
```bash
[teguh@redhat1 deploy-inventory]$ ansible ungrouped -i inventory --list-hosts
  hosts (1):
    redhat1.mshome.net

[teguh@redhat1 deploy-inventory]$ ansible backend -i inventory --list-hosts
  hosts (1):
    redhat3.mshome.net
[teguh@redhat1 deploy-inventory]$ ansible frontend -i inventory --list-hosts
  hosts (1):
    redhat2.mshome.net
[teguh@redhat1 deploy-inventory]$ ansible app -i inventory --list-hosts
  hosts (2):
    redhat2.mshome.net
    redhat3.mshome.net
```