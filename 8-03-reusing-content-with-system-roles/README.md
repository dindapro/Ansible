# role-system

## Install

```bash
[student@workstation role-system]$ sudo yum install rhel-system-roles
```

## Verify

```bash
[student@workstation role-system]$ ansible-galaxy list
```

## HELP








## Execute Playbook
```bash
[student@workstation role-system]$ ansible-playbook configure_time.yml
```

## Check date
```bash
[student@workstation role-system]$ ansible database_servers -m shell -a date
```