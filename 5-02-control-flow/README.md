# Writing Loops and Conditional Tasks

## Run
```bash
$ ansible-playbook playbook.yml
```

## Check
```bash
$ ansible redhat1.mshome.net -m command \
 -a 'cat /etc/redhat-release' -u devops --become
```

## Run
```bash
$ ansible-playbook playbook-v2.yml
```