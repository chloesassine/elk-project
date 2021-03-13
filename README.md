## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Link Name](Images/Final-Network-Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of yml and config file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.
- Load balances divert traffic in order to protect the integrety of a system from DDoS attcks. 
- A jump box provides a single node that the user can monitor.  

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- Filebeat watches information in a file system and can identify what changes have been made and then they occured. 
- Metricbeat records metrics and statistics and is able to collact the information in order to output to a source. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web1     | Web Server|10.0.0.5   | Linux            |
| Web2     | Web Server|10.0.0.7   |Linux             |
| ELK      |Elk Server|10.1.0.4    |Linux             |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Elk Server machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 13.76.84.223

Machines within the network can only be accessed by Jump-Box-Provisioner.
- 1.159.104.31

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
|Jump Box | No                  | Workstation Public IP on port 22 SSH|
|Web1     |No                   |                      |
|Web2      |No                   |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- commands can be run onto multiple servers at various times, using a playbook.  

The playbook implements the following tasks:
- install docker.io
- install python-pip
- install docker 
- run sysctl -w vm.max_mao_count=262144
- launch docker container elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

- Web1: 10.0.0.5
- Web2: 10.0.0.7

We have installed the following Beats on these machines:

- Web1, Web2 and ELK Server
- ELK Stack Installed Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- To collect the data of changes made to the machine is done by Filebeats and Metricbeats. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

- _Which file is the playbook? Where do you copy it?_ 
- /etc/ansible/files/filebeat-configuration.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ 
- /etc/ansible/host file in order to add webserver/elkserver ip addresses. 
- _Which URL do you navigate to in order to check that the ELK server is running? 
- Kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
- ansible-playbook filebeat-playbook.yml
