# Managing Secrets

## Generate
```bash
$ password=$(ansible -m debug -a msg="{{ 'redhat'  | password_hash('sha512') }}" localhost | awk '/msg/ {print $NF}' | sed 's/^"//' | sed 's/"$//')
$ echo $password
$6$3CtETWbfzG3rVYol$huM76VZx2jB5fo1WVaxdWapfVEwopol78tcuJH9NMskBvszOnMf1ZwnGW/mJjtCC0dgt7Piot4tvS4N9pkCJu1
```

## Create
```bash
$ ansible-vault create secret.yml
New Vault password: 
Confirm New Vault password:
```

## Edit
```bash
$ ansible-vault view secret.yml
Vault password: 
username: ansibleuser1
pwhash: $6$3CtETWbfzG3rVYol$huM76VZx2jB5fo1WVaxdWapfVEwopol78tcuJH9NMskBvszOnMf1ZwnGW/mJjtCC0dgt7Piot4tvS4N9pkCJu1
```

## Syntax Check
```bash
$ ansible-playbook create-users.yml \
 --syntax-check \
 --ask-vault-pass
```

## Execute 
```bash
$ ansible-playbook create-users.yml \
 --vault-password-file=vault-pass
```
