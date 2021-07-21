# Install

Install ansible package
```bash
[teguh@redhat1 ~]$ sudo yum install ansible
```

Check version ansible
```bash
[teguh@redhat1 ~]$ ansible --version
ansible 2.9.23
  config file = /etc/ansible/ansible.cfg
  configured module search path = ['/home/teguh/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3.6/site-packages/ansible
  executable location = /usr/bin/ansible
  python version = 3.6.8 (default, Aug 18 2020, 08:33:21) [GCC 8.3.1 20191121 (Red Hat 8.3.1-5)]
```

Check version python
```bash
[teguh@redhat1 ~]$ ansible localhost -m setup | grep ansible_python_version
        "ansible_python_version": "3.6.8",
```
