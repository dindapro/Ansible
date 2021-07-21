# Deploying Custom Files with Jinja2 Templates

## Run motd.yml

```bash
[student@workstation file-template]$ ansible-playbook motd.yml
```

## Verify

```bash
[student@workstation file-template]$ ssh devops@servera.lab.example.com
This is the system servera.lab.example.com.
This is a RedHat version 8.0 system.
Only use this system with permission.
You can request access from clyde@example.com.
...output omitted...
[devops@servera ~]# exit
Connection to servera.lab.example.com closed.
```