# 

##
```bash
$ ansible-galaxy init myvhost
```

##
```bash
$ rm -rvf myvhost/{defaults,vars,tests}
```

##
```bash
ansible all -a \
 'cat /etc/httpd/conf.d/vhost.conf'
```

##
```bash
$ ansible all -m uri \
 -a 'url=http://localhost return_content=true'
```