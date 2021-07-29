# deploy-manage

## create ansible.cfg
```bash
$ vi ansible.cfg
```

## create inventory
```bash
$ vi inventory
```

## privilege escalation
```bash
$ ansible app -i inventory --list-hosts
```

## privilege escalation edit ansible.cfg
```bash
[defaults]
inventory = ./inventory

[privilege_escalation]
become = true
become_method = sudo
become_user = root
become_ask_pass = true
```

## Test
```bash
$ ansible app -i inventory --list-hosts
BECOME password:
```
