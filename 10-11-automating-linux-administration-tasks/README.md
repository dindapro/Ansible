# Automating Linux Administration Tasks

## Goal

You should be able to create playbooks for configuring on a managed host a 
* software repository, 
* users and groups, 
* logical volumes, 
* cron jobs, and 
* additional network interfaces.

## Run playbook
```bash
[student@workstation system-review]$ ansible-playbook repo_playbook.yml
```

```bash
[student@workstation system-review]$ mkdir vars
[student@workstation system-review]$ vi vars/users_vars.yml
```