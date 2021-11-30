# Project--1-ELKstackserver
ELK stack server setup Kibana filebeat and metricbeat playbook, diagram of the machineAutomated ELK Stack Deployment
The files in this repository were used to configure the network depicted below.

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![/c/Users/cfppr/Desktop/ELK-machine-diagram1.png](Images/diagram_filename.png)



These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

  -filebeatplaybook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly availabel, in addition to restricting unauthorized access to the network.
- Load balancer protect the avaibility of the data by distributing the load accross multiple servers. Load balancer protect the servers from a denial of service attack. Load balancer distributes traffic amongst the servers. 
 Jump boc is a secure computer that all admin first connect to before launching any administrative task or use as an origination point to connect to other server or untursted enviornments.Jump box is to limit access to servers that are not accessible from the interenet, except thrh the jump box.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the server metrics and system logs.
Filebeat records system logs, such as logon attempts. Log files monitered by filebeat.
Metricbeat records metric data, such as cpu change.


The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 20.70.197.194   | Linux            |
| Red-Team web-1  |  DVWA server  Filebeat and metricbeat       | 10.1.0.5           |                  |
| Red-Team wen-2  |  DVWA server File beat and Metric beat        |10.1.0.6            |                  |
| ELK-VM  |  ELK server Kibana      |   20.37.5.120 PRIVATE IP-10.2.0.4
         |                  |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- jumpbox SSH publicIP : 20.211.104.94


Machines within the network can only be accessed by the Red team -Jump box gateway mchine
- Red team web-1 and web-2  allow to access ELK VM. What was its IP address web-1 10.1.0.5   web-2 10.1.0.6_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes              | 20.70.197.194    |
| elk -vm         |Yes                     | 20.37.5.120                     |
|  web-1        | No                    |   10.1.0.5                   |
web-2             |No                    | 10.1.0.6
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible is Human readable automaiton. No special skills needed . Tasks ececuted in order. Get productive quickly.  Powerful  App deployment. COnfiguration management. Uses Opne SSH and winRM. no agents to ecploit or updat.
 
The playbook implements the following tasks:

- Install docker 
 -install Python3-pip
- Increase Virtual memory
- Download and launch the elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- web-1 10.1.0.5   web-2 10.1.0.6

We have installed the following Beats on these machines:
- web-1_-Filebeat and on web-2-metricbeat 


These Beats allow us to collect the following information from each machine:
- Filebeat forwards and centralizes log data from your target machines. It monitors the log files that you specify, ie. server logs such as login attempts. It collects the log events, then forwards the data to the ELK server.

- Metricbeat collects the machine metrics and statistical data, such as CPU usage, memory usage and inbound/outbound traffic and sends the data to the ELK server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the configuration and playbook YAML files  to /etc/ansible/roles/filebeat.yml and metricbeat.yml
- Update the /etc/ansible/hosts files with two speerate wections of the ip adresses of ELK server and the webservers on the interenet networks. provide the ip adresses which we mention in our table . two sections[wecservers][elkservers] 
- upeate plybooks of filebeat.yml and metricbeat.yml each to point to the ELK servers ip address, username and password

- Run the playbook, and navigate to container and ssh in to webservers to check that the installation worked as expected.



- YAML file is the playbook. We copy /etc/ansible/playbook
- /etc/ansible/hosts file we update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- URL http://[your.IP]:5601 navigate to in order to check that the ELK server is running.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

playbook is in the /etc/ansible/playbook files
before we make playbook we have to update the /etc/ansible/ansible.config
etc/ansible/hosts files.
to run the playbook ansible-playbook playbookname with .yml extension.
