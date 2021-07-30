# Ansible Training 

## enable environment

```bash
sudo umount /mnt/d
sudo mount -t drvfs D: /mnt/d -o metadata,uid=1000,gid=1000,umask=22,fmask=111,wfd=8
mount -l
source ~/virtualenvs/ansible/bin/activate
```

## Edit 
```powershell
Get-NetIPInterface | where {$_.InterfaceAlias -eq 'vEthernet (WSL)' -or $_.InterfaceAlias -eq 'vEthernet (Default Switch)'} | Set-NetIPInterface -Forwarding Enabled

```

## Setup keygen

generate keygen
```bash
[teguh@redhat1 ~]$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/teguh/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/teguh/.ssh/id_rsa.
Your public key has been saved in /home/teguh/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:92AyEFLcLF4YjzG7LTE1eI/VunNH6GSxXu6MB84WEcU teguh@redhat1.local
The key's randomart image is:
+---[RSA 3072]----+
|    .o**o  . o.  |
|     .=O=.. + E  |
|     .*+.+ . =   |
|      .*. o * o  |
|      o S +* =   |
|       . =oo* o  |
|           =.B   |
|            = +  |
|           . .   |
+----[SHA256]-----+

```


setup Host managed

```bash
[teguh@redhat1 ~]$ ssh-copy-id -i ~/.ssh/id_rsa.pub localhost
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/teguh/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
teguh@localhost's password:

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'localhost'"
and check to make sure that only the key(s) you wanted were added.




[teguh@redhat1 ~]$ ssh-copy-id -i ~/.ssh/id_rsa.pub 172.27.88.52
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/teguh/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
teguh@172.27.88.52's password:

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh '172.27.88.52'"
and check to make sure that only the key(s) you wanted were added.


[teguh@redhat1 ~]$ ssh-copy-id -i ~/.ssh/id_rsa.pub 172.27.81.212
[teguh@redhat1 ~]$

```