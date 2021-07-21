# Create User

Generate password 
https://access.redhat.com/solutions/221403

```bash
password=$(ansible -m debug -a msg="{{ 'operation'  | password_hash('sha512') }}" localhost | awk '/msg/ {print $NF}' | sed 's/^"//' | sed 's/"$//')

echo $password
```

## Basic
```bash
[teguh@redhat1 deploy-adhoc]$ ansible all -m user -a 'name=devops uid=4000 state=present password=$6$3zTI4qijpjo2NJHN$74qF96aTCoUKvTwNhTWAS/CPiD6S707X/9Q8wX/265d1Lq7cSW5.Wj7yOFF0FfdZ2nkI95tvlfwSJmWFYyZGe0' --become -K
BECOME password:
redhat2.mshome.net | CHANGED => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "append": false,
    "changed": true,
    "comment": "",
    "group": 4000,
    "home": "/home/devops",
    "move_home": false,
    "name": "devops",
    "password": "NOT_LOGGING_PASSWORD",
    "shell": "/bin/bash",
    "state": "present",
    "uid": 4000
}
redhat3.mshome.net | CHANGED => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "append": false,
    "changed": true,
    "comment": "",
    "group": 4000,
    "home": "/home/devops",
    "move_home": false,
    "name": "devops",
    "password": "NOT_LOGGING_PASSWORD",
    "shell": "/bin/bash",
    "state": "present",
    "uid": 4000
}
redhat1.mshome.net | CHANGED => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/libexec/platform-python"
    },
    "append": false,
    "changed": true,
    "comment": "",
    "group": 4000,
    "home": "/home/devops",
    "move_home": false,
    "name": "devops",
    "password": "NOT_LOGGING_PASSWORD",
    "shell": "/bin/bash",
    "state": "present",
    "uid": 4000
}

```

