# Install

## Install ansible package
```bash
$ sudo yum install ansible
```

## Check Ansible
```bash
$ ansible --version
```

## Check Python
```bash
$ ansible localhost -m setup | grep ansible_python_version
```
