# AnsiblePlaybooks
This repository contains ansible playbooks. These playbooks are used to deploy the RTvsBT network.  
To run a seperate playbook:  
`ansible-playbook -i hosts.ini playbooks/<playbook>.yml`  

To deploy the full network:  
`ansible-playbook -i hosts.ini playbooks/DeployNetwork.yml`  

To change the default credentials of the machine check out the hosts.ini file.  

## Network



THe current network contains the following machines

### Deploy: Ansible
Description:  This server deploys all the other servers.  
Hostname:     Ansible01  
IP:           192.168.1.xxx  
OS:           Ubuntu 20.0  

### Siem: ELK stack
Description:  This server is responsible for the Log storage and dashboard. It uses an ELK stack ran with docker.  
Hostname:     Siem01  
IP:           192.168.1.xxx  
Playbook:     playbook/xxx  
OS:           Ubuntu 20.0  
Notes:        Kibana dashboard is accessible on port 5601.  

### Ticketing: Zammad
Description:  This server is responsible for the zammad ticketing system. It uses docker for the installation.  
Hostname:     Zammad01  
IP:           192.168.1.xxx  
Playbook:     playbook/xxx  
OS:           Ubuntu 20.0  

### NIDS: Suricata
Description:  This server investigates the network traffic with suricata and alerts intrusions.  
Hostname:     Nids01  
IP:           192.168.1.xxx  
Playbook:     playbook/xxx  
OS:           Ubuntu 20.0  
Notes:        Filebeat is used to upload the logs to the elastic search server.  

### HIDS: Wazuh
Description:  This server acts as the manager for the wazuh clients. The clients generate alerts, The manager then collects all the alerts.  
Hostname:     Hids01  
IP:           192.168.1.xxx  
Playbook:     playbook/xxx  
OS:           Ubuntu 20.0  
Notes:        Filebeat is used to upload the logs to the elastic search server.  

### Attack machine
Description:  This server contains the red team dashboard.  
Hostname:     Redteam01  
IP:           192.168.1.xxx  
Playbook:     playbook/xxx  
OS:           Kali linux  
Notes:        This server contains both the redteam frontend and backend. It also has the automated attack script.  

### Vulnerable machine 1
Description:  This machine hosts the defense vulnerable webapp & is used in the ransomware attack.  
Hostname:     Defensie-Web01  
IP:           192.168.1.xxx  
Playbook:     playbook/xxx  
OS:           Ubuntu 20.0  
Notes:        Uses the wazuh agent to send the logs to the wazuh manager.  

### Vulnerable machine 2
Description:  This machine contains a user that is part of the lxd group.
Hostname:     Defensie-Lxd01  
IP:           192.168.1.xxx  
Playbook:     playbook/xxx  
OS:           Ubuntu 20.0  
Notes:        This machine contains a user that is part of the lxd group, which can be used to escalate privileges.  
