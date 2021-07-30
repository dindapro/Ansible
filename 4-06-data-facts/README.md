# Managing Facts

## Ad hoc fact
```bash
$ ansible webserver -m setup | grep ansible_local
        "ansible_local": {},
```

## Install
```bash
$ ansible-playbook setup_facts.yml
```

## Check
```bash
$ ansible webserver -m command \
 -a 'systemctl status httpd'
```

## Playbook
```bash
$ ansible-playbook playbook.yml
```