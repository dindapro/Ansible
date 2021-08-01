# role-system

## Install

```bash
[student@workstation role-system]$ sudo yum install linux-system-roles
```

## Verify

```bash
[student@workstation role-system]$ ansible-galaxy list
```

## HELP
This is the correct way install on ansible with ENV
```bash
(ansible) teguh@TeguhF:/mnt/d/02-IT/05-RedH/2-Ans/2-Cod/8-03-role-system$ pip3 install jmespath
```






## Execute Playbook
```bash
[student@workstation role-system]$ ansible-playbook configure_time.yml
```

## Check date
```bash
[student@workstation role-system]$ ansible database_servers -m shell -a date
```