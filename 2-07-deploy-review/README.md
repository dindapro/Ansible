# Deploying Ansible 

## Verify
```bash
$ sudo yum list installed ansible
$ ansible --version
```

## Copy
```bash
$ ansible all -m copy -a 'content="This server is managed by Ansible.\n" dest=/etc/motd' -b
redhat1.mshome.net | CHANGED
redhat2.mshome.net | CHANGED
redhat3.mshome.net | CHANGED
```

## Re-run
```bash
$ ansible all -m copy -a 'content="This server is managed by Ansible.\n" dest=/etc/motd' -b
redhat1.mshome.net | SUCCESS
redhat2.mshome.net | SUCCESS
redhat3.mshome.net | SUCCESS
```

## Cat
```bash
$ ansible all -m command -a 'cat /etc/motd'
```