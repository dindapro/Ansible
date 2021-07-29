# Deploying ansible 

## verify ansible 

```bash

teguh@redhat1 deploy-adhoc]$ sudo yum list installed ansible
[sudo] password for teguh:
Updating Subscription Management repositories.
Installed Packages
ansible.noarch      2.9.23-1.el8ae      @ansible-2.9-for-rhel-8-x86_64-rpms
[teguh@redhat1 deploy-adhoc]$

[teguh@redhat1 deploy-adhoc]$ ansible --version
ansible 2.9.23
  config file = /home/teguh/deploy-adhoc/ansible.cfg
  configured module search path = ['/home/teguh/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3.6/site-packages/ansible
  executable location = /usr/bin/ansible
  python version = 3.6.8 (default, Aug 18 2020, 08:33:21) [GCC 8.3.1 20191121 (Red Hat 8.3.1-5)]
[teguh@redhat1 deploy-adhoc]$


```

## Create ansible.cfg and inventory 

```bash
[teguh@redhat1 ~]$ mkdir deploy-review
[teguh@redhat1 ~]$ cd deploy-review


[teguh@redhat1 deploy-review]$ cat inventory/inventory

[internetweb]
redhat1.mshome.net
[intranetweb]
redhat2.mshome.net
redhat3.mshome.net


[teguh@redhat1 deploy-review]$ cat ansible.cfg

[defaults]
inventory=inventory
remote_user=devops

[privilege_escalation]
become = false
become_method = sudo
become_user = root
become_ask_pass = false

```

## execute command copy

```bash
[teguh@redhat1 deploy-review]$ ansible all -m copy -a 'content="This server is managed by Ansible.\n" dest=/etc/motd' -b
redhat3.mshome.net | CHANGED => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": true,
    "checksum": "93d304488245bb2769752b95e0180607effc69ad",
    "dest": "/etc/motd",
    "gid": 0,
    "group": "root",
    "md5sum": "af74293c7b2a783c4f87064374e9417a",
    "mode": "0644",
    "owner": "root",
    "secontext": "system_u:object_r:etc_t:s0",
    "size": 35,
    "src": "/home/devops/.ansible/tmp/ansible-tmp-1626770101.2616215-15370-72501516683859/source",
    "state": "file",
    "uid": 0
}
redhat2.mshome.net | CHANGED => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": true,
    "checksum": "93d304488245bb2769752b95e0180607effc69ad",
    "dest": "/etc/motd",
    "gid": 0,
    "group": "root",
    "md5sum": "af74293c7b2a783c4f87064374e9417a",
    "mode": "0644",
    "owner": "root",
    "secontext": "system_u:object_r:etc_t:s0",
    "size": 35,
    "src": "/home/devops/.ansible/tmp/ansible-tmp-1626770101.2368877-15369-27889484881746/source",
    "state": "file",
    "uid": 0
}
redhat1.mshome.net | CHANGED => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/libexec/platform-python"
    },
    "changed": true,
    "checksum": "93d304488245bb2769752b95e0180607effc69ad",
    "dest": "/etc/motd",
    "gid": 0,
    "group": "root",
    "md5sum": "af74293c7b2a783c4f87064374e9417a",
    "mode": "0644",
    "owner": "root",
    "secontext": "system_u:object_r:etc_t:s0",
    "size": 35,
    "src": "/home/devops/.ansible/tmp/ansible-tmp-1626770101.2109132-15367-125244029500236/source",
    "state": "file",
    "uid": 0
}

```

## reexecute command return success

```bash

[teguh@redhat1 deploy-review]$ ansible all -m copy -a 'content="This server is managed by Ansible.\n" dest=/etc/motd' -b
redhat2.mshome.net | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "checksum": "93d304488245bb2769752b95e0180607effc69ad",
    "dest": "/etc/motd",
    "gid": 0,
    "group": "root",
    "mode": "0644",
    "owner": "root",
    "path": "/etc/motd",
    "secontext": "system_u:object_r:etc_t:s0",
    "size": 35,
    "state": "file",
    "uid": 0
}
redhat3.mshome.net | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "checksum": "93d304488245bb2769752b95e0180607effc69ad",
    "dest": "/etc/motd",
    "gid": 0,
    "group": "root",
    "mode": "0644",
    "owner": "root",
    "path": "/etc/motd",
    "secontext": "system_u:object_r:etc_t:s0",
    "size": 35,
    "state": "file",
    "uid": 0
}
redhat1.mshome.net | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/libexec/platform-python"
    },
    "changed": false,
    "checksum": "93d304488245bb2769752b95e0180607effc69ad",
    "dest": "/etc/motd",
    "gid": 0,
    "group": "root",
    "mode": "0644",
    "owner": "root",
    "path": "/etc/motd",
    "secontext": "system_u:object_r:etc_t:s0",
    "size": 35,
    "state": "file",
    "uid": 0
}

```

## check all /etc/motd

```bash
[teguh@redhat1 deploy-review]$ ansible all -m command -a 'cat /etc/motd'
redhat2.mshome.net | CHANGED | rc=0 >>
This server is managed by Ansible.
redhat3.mshome.net | CHANGED | rc=0 >>
This server is managed by Ansible.
redhat1.mshome.net | CHANGED | rc=0 >>
This server is managed by Ansible.

```