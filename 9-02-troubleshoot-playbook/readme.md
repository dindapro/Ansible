#

##
```bash

```

##
```bash
(ansible) teguh@TeguhF:/mnt/d/02-IT/05-RedH/2-Ans/2-Cod/9-02-troubleshoot-playbook/finish$ ansible-playbook samba.yml --step

PLAY [Install a samba server] ********************************************************************************************************
Perform task: TASK: Gathering Facts (N)o/(y)es/(c)ontinue: y

Perform task: TASK: Gathering Facts (N)o/(y)es/(c)ontinue: ***************************************************************************

TASK [Gathering Facts] ***************************************************************************************************************
ok: [redhat1.mshome.net]
Perform task: TASK: install samba (N)o/(y)es/(c)ontinue: y

Perform task: TASK: install samba (N)o/(y)es/(c)ontinue: *****************************************************************************

TASK [install samba] *****************************************************************************************************************
ok: [redhat1.mshome.net]
Perform task: TASK: install firewalld (N)o/(y)es/(c)ontinue: y

Perform task: TASK: install firewalld (N)o/(y)es/(c)ontinue: *************************************************************************

TASK [install firewalld] *************************************************************************************************************
ok: [redhat1.mshome.net]
Perform task: TASK: debug install_state variable (N)o/(y)es/(c)ontinue: y

Perform task: TASK: debug install_state variable (N)o/(y)es/(c)ontinue: **************************************************************

TASK [debug install_state variable] **************************************************************************************************
ok: [redhat1.mshome.net] => {
    "msg": "The statefor the sambaservice is installed"
}
Perform task: TASK: start samba (N)o/(y)es/(c)ontinue: y

Perform task: TASK: start samba (N)o/(y)es/(c)ontinue: *******************************************************************************

TASK [start samba] *******************************************************************************************************************
ok: [redhat1.mshome.net]
Perform task: TASK: start firewalld (N)o/(y)es/(c)ontinue: y

Perform task: TASK: start firewalld (N)o/(y)es/(c)ontinue: ***************************************************************************

TASK [start firewalld] ***************************************************************************************************************
ok: [redhat1.mshome.net]
Perform task: TASK: configure firewall for samba (N)o/(y)es/(c)ontinue: y

Perform task: TASK: configure firewall for samba (N)o/(y)es/(c)ontinue: **************************************************************

TASK [configure firewall for samba] **************************************************************************************************
ok: [redhat1.mshome.net]
Perform task: TASK: deliver samba config (N)o/(y)es/(c)ontinue: y

Perform task: TASK: deliver samba config (N)o/(y)es/(c)ontinue: **********************************************************************

TASK [deliver samba config] **********************************************************************************************************
changed: [redhat1.mshome.net]

PLAY RECAP ***************************************************************************************************************************
redhat1.mshome.net         : ok=8    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

(ansible) teguh@TeguhF:/mnt/d/02-IT/05-RedH/2-Ans/2-Cod/9-02-troubleshoot-playbook/finish$ 
```