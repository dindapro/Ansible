# adhoc command

## prepare directory

```bash
[teguh@redhat1 ~]$ mkdir deploy-adhoc/
[teguh@redhat1 ~]$ cd deploy-adhoc/
```

### create ansible.cfg and inventory file 

```bash
[teguh@redhat1 deploy-adhoc]$ cat ansible.cfg
[defaults]
inventory=inventory

[teguh@redhat1 deploy-adhoc]$ cat inventory
[control_node]
redhat1.mshome.net
[frontend]
redhat2.mshome.net

```

## ad hoc command 

### ping module 
```bash
[teguh@redhat1 deploy-adhoc]$ ansible all -m ping

redhat1.mshome.net | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/libexec/platform-python"
    },
    "changed": false,
    "ping": "pong"
}
redhat2.mshome.net | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
}

```


### command

```bash
[teguh@redhat1 deploy-adhoc]$ ansible control_node -m command -a 'id'
redhat1.mshome.net | CHANGED | rc=0 >>
uid=1000(teguh) gid=1000(teguh) groups=1000(teguh),10(wheel) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
```

### command with root user

```bash
[teguh@redhat1 deploy-adhoc]$ ansible control_node -m command -a 'id' -b -K
BECOME password: teguh
redhat1.mshome.net | CHANGED | rc=0 >>
uid=0(root) gid=0(root) groups=0(root) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
```

### command with devops user 
```bash

[teguh@redhat1 deploy-adhoc]$ ansible all -m command -a 'id' -u 'devops'
redhat1.mshome.net | CHANGED | rc=0 >>
uid=4000(devops) gid=4000(devops) groups=4000(devops) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
redhat2.mshome.net | CHANGED | rc=0 >>
uid=4000(devops) gid=4000(devops) groups=4000(devops) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
redhat3.mshome.net | CHANGED | rc=0 >>
uid=4000(devops) gid=4000(devops) groups=4000(devops) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023

```

## copy without --become

### Error because not privilege escalation

```bash
[teguh@redhat1 deploy-adhoc]$ ansible control_node -m copy -a 'content="Managed by Ansible\n" dest=/etc/motd' -u 'devops'
redhat1.mshome.net | FAILED! => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/libexec/platform-python"
    },
    "changed": false,
    "checksum": "4458b979ede3c332f8f2128385df4ba305e58c27",
    "msg": "Destination /etc not writable"
}

```

### Success with --become

```bash
[teguh@redhat1 deploy-adhoc]$ ansible control_node -m copy -a 'content="Managed by Ansible\n" dest=/etc/motd' -u 'devops' --become
redhat1.mshome.net | CHANGED => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/libexec/platform-python"
    },
    "changed": true,
    "checksum": "4458b979ede3c332f8f2128385df4ba305e58c27",
    "dest": "/etc/motd",
    "gid": 0,
    "group": "root",
    "md5sum": "65a4290ee5559756ad04e558b0e0c4e3",
    "mode": "0644",
    "owner": "root",
    "secontext": "system_u:object_r:etc_t:s0",
    "size": 19,
    "src": "/home/devops/.ansible/tmp/ansible-tmp-1626768986.4973764-14674-179616196268683/source",
    "state": "file",
    "uid": 0
}
[teguh@redhat1 deploy-adhoc]$ cat /etc/motd
Managed by Ansible

```

### rerun ad hoc with success response 

```bash
[teguh@redhat1 deploy-adhoc]$ ansible control_node -m copy -a 'content="Managed by Ansible\n" dest=/etc/motd' -u 'devops' --become
redhat1.mshome.net | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/libexec/platform-python"
    },
    "changed": false,
    "checksum": "4458b979ede3c332f8f2128385df4ba305e58c27",
    "dest": "/etc/motd",
    "gid": 0,
    "group": "root",
    "mode": "0644",
    "owner": "root",
    "path": "/etc/motd",
    "secontext": "system_u:object_r:etc_t:s0",
    "size": 19,
    "state": "file",
    "uid": 0
}

```