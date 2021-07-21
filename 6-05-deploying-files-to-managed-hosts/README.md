# Deploying Files to Managed Hosts

## check ansible_processor_count

```bash
[student@workstation file-review]$ ansible serverb.lab.example.com -m setup
serverb.lab.example.com | SUCCESS => {
    "ansible_facts": {
...output omitted...
	"ansible_processor_count": 1,
...output omitted...
	"ansible_memtotal_mb": 821,
...output omitted...
    },
    "changed": false
}
```

## Run playbook
```bash

[student@workstation file-review]$ ansible-playbook motd.yml
```

## Verify 

```bash
[student@workstation file-review]$ ssh devops@serverb.lab.example.com
*------------------------------- PRIVATE SYSTEM -----------------------------*
*   Access to this computer system is restricted to authorised users only.   *
*                                                                            *
*      Customer information is confidential and must not be disclosed.       *
*----------------------------------------------------------------------------*
System total memory: 821 MiB.
System processor count: 1
Activate the web console with: systemctl enable --now cockpit.socket

Last login: Thu Apr 25 22:09:33 2019 from 172.25.250.9
[devops@serverb ~]$ logout
```