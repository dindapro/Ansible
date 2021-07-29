# adhoc command

## ping module 
```bash
$ ansible all -m ping
```

## command
```bash
$ ansible control_node -m command -a 'id'
```

## Become and Ask Password
```bash
$ ansible control_node -m command -a 'id' -b -K
BECOME password: 
```

## User
```bash
$ ansible all -m command -a 'id' -u 'devops'
```

## Error
```bash
$ ansible control_node -m copy -a 'content="Managed by Ansible\n" dest=/etc/motd' -u 'devops'
redhat1.mshome.net | FAILED!
```

## Success

```bash
$ ansible control_node -m copy -a 'content="Managed by Ansible\n" dest=/etc/motd' -u 'devops' --become
redhat1.mshome.net | CHANGED 
```
## Test
```bash
$ cat /etc/motd
```

## Re-run

```bash
$ ansible control_node -m copy -a 'content="Managed by Ansible\n" dest=/etc/motd' -u 'devops' --become
redhat1.mshome.net | SUCCESS
```