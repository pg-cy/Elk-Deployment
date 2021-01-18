# Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![elk diagram](images/ELK+network.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook files may be used to install only certain pieces of it, such as Filebeat.



This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures redundancy, in addition to restricting access to the network.
- Load balancers route requests from external hosts to webservers ensuring they are not being overloaded (which can cause them to crash or be inaccessable). 

- A jump-box is another layer of security. Users can gain access to a network only by SSH to a jump-box machine that has a public facing address, from there one can move throughout the network.   

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the applications and system logs.
- Filebeat watches for changes to syslog and Authentication log



The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function  | IP Address | Operating System |
|----------|-----------|------------|------------------|
| Jump Box | Gateway   |  10.0.0.4  | Linux            |
| web1     |   dvwa    |  10.0.0.5  | Linux            |
| web2     |   dvwa    |  10.0.0.6  | Linux            |
| elk      |moniter VMs|  10.1.0.5  | Linux            |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump-box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

- A)Any ip address that has access to the private ssh key will be allowed to ssh into jumpbox.
VM Machines within the network can only be accessed by the Jump-box ansible container through ssh.

-The ELK VM (10.1.0.5) can only be accessed by the Jump-box ansible container(10.0.0.5) which contains the ssh private key.


A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses                 |
|----------|---------------------|--------------------------------------|
| Jump Box | Yes(168.62.194.182) | External host containing ssh-priv-key|
|Web1 &web2| no                  |  jumpbox(10.0.0.4)                   |
|   elk    | no                  |  jumpbox(10.0.0.4)                   |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

- A) The main advantage of automating this process is to quickly reconfigure a machine. If multiple VMs was newly created or a previous VM had to be destroyed, we can simply run the playbook to reconfigure out machines. This saves us time rather than manually accessing each machine to install/configuring.

The ELK playbook implements the following tasks:
- Increases virtual memory for our ELK server to use.
- Installs docker
- Installs python3 and installs the module docker for python
- Downloads the elk image and installs it on a docker container with specific ports for elk to use.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance. (navigate to your elk server and run the following,  docker ps -a)

![elk display status](images/elk_docker_display.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- A) Web1 and web2 machines are being monitored.

We have installed the following Beats on these machines:
- A) Filebeat was installed on web1 and web2 machines

These Beats allow us to collect the following information from each machine:
- A) Filebeat collects data from the syslog and auth logs. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy/download the "install-elk.yml", "filebeat-config.yml","filebeat-playbook" file onto your ansible container.
- Edit the "hosts" file (/etc/ansible/hosts) to include our elk server/VMs for ansible to use playbooks on.
![hosts edit file](images/hosts_edit.png)
- Run the "install-elk.yml" playbook (note that the remote_user inside the file has to be the user created for ssh keys to your elk server)
- edit the "filebeat-config.yml" file to send the data to our ELK server. (IP needs to be the ELK server)
![filebeat config edit](images/IP_change_filebeat_configP1.png)
![filebeat config edit](images/IP_change_filebeat_configP2.png)
- run the "filebeat-playbook"


Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?

- A) You need to update the "hosts" file and add your webservers/elk ip addresses. This allows ansilbe to run playbooks on specific machines such as installing dvwa,filebeat or elk on the specified IP addresses from the hosts file. In the installation of filebeat,  you will have to modify the "filebeat-config.yml" file to point it to our elk server. During the installation process this file will be copied and renamed filebeat.yml to the machines we want to monitor.

Which URL do you navigate to in order to check that the ELK server is running?

- A) Navigate to 52.151.193.28:5601 in a browser to access kibana



 

>>>>>>> 623af73961c880bfce855ab58a463673338ded55
