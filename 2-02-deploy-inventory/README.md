# deploy-inventory

## Edit hosts
```bash
$ sudo vi /etc/ansible/hosts
```

## check --list-hosts
```bash
$ ansible all --list-hosts
```

## ungrouped and group
```bash
$ ansible ungrouped --list-hosts
$ ansible client --list-hosts
```

## create inventory file 
```bash
$ vi inventory
```

## List all inventory hosts
```bash
$ ansible all -i inventory --list-hosts
```
## check group and ungrouped 
```bash
$ ansible ungrouped -i inventory --list-hosts

$ ansible backend -i inventory --list-hosts

$ ansible frontend -i inventory --list-hosts

$ ansible app -i inventory --list-hosts
```