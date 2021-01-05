# Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures redundancy, in addition to restricting access to the network.
-Load balancers route requests from external hosts to webservers ensuring they are not being overloaded (which can cause them to crash or be inaccessable). 

-A jump-box is another layer of security. Users can gain access to a network only by SSH to a jump-box machine that has a public facing address, from there one can move throughout the network.   

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the applications and system logs
A)filebeat watches for changes to syslog and Authentication log



The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function  | IP Address | Operating System |
|----------|-----------|------------|------------------|
| Jump Box | Gateway   |  10.0.0.4  | Linux            |
| web1     |   dvwa    |  10.0.0.5  | Linux            |
| web2     |   dvwa    |  10.0.0.6  | Linux            |
| elk      |moniter VMs|  10.1.0.5  | Linux            |
|	   |(web1&web2)|  	    |		       |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump-box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
A)Any ip address that has access to the private ssh key will be allowed to ssh into jumpbox.
Machines within the network can only be accessed by the Jump-box ansible container through ssh.

-The ELK VM (10.1.0.5) can only be accessed by the Jump-box (10.0.0.5) ansible container which contains the ssh private key.


A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses                 |
|----------|---------------------|--------------------------------------|
| Jump Box | Yes                 | External host containing ssh-key)    |
|Web1 &web2| no                  |  jumpbox(10.0.0.4)                   |
|   elk    | no                  |  jumpbox(10.0.0.4)                   |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

-
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
A)web1 and web2 machines are being monitored.

We have installed the following Beats on these machines:
A) filebeat was installed on web1 and web2 machines

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
A)
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?
A)52.151.193.28:5601 

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
=======
this is a test!
 
![test image](images/Peter_gentile_Homework_12.jpg)
>>>>>>> 623af73961c880bfce855ab58a463673338ded55
