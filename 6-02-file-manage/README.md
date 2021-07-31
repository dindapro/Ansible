# Modifying and Copying Files to Hosts



## Run secure_log_backups.yml
```bash
[student@workstation file-manage]$ ansible-playbook secure_log_backups.yml
```

## Verify

```bash
[student@workstation file-manage]$ tree -F secure-backups
```

## run copy_file.yml

```bash
[student@workstation file-manage]$ ansible-playbook copy_file.yml
```

## Verify

```bash
[student@workstation file-manage]$ ansible all -m command -a 'ls -Z' -u devops
```

## Run selinux_defaults.yml

```bash
[student@workstation file-manage]$ ansible-playbook selinux_defaults.yml
```

## Verify 

```bash
[student@workstation file-manage]$ ansible all -m command -a 'ls -Z' -u devops
```

## Run add_line.yml

```bash
[student@workstation file-manage]$ ansible-playbook add_line.yml
```

## Verify 

```bash
[student@workstation file-manage]$ ansible all -m command \
> -a 'cat users.txt' -u devops
```

## Run add_block.yml

```bash

[student@workstation file-manage]$ ansible-playbook add_block.yml
```

## Verify 

```bash
[student@workstation file-manage]$ ansible all -m command \
> -a 'cat users.txt' -u devops
```

## Run remove_file.yml

```bash

[student@workstation file-manage]$ ansible-playbook remove_file.yml
```

## Verify 

```bash
[student@workstation file-manage]$ ansible all -m command -a 'ls -l'
```