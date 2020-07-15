## Automated ELK Stack Deployment# Ansible-Provisioner
The files in this repository were used to configure the network depicted below.

! [Project 1 Diagram] (Project-1-Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either 
recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to 
install only certain pieces of it, such as Filebeat.

  - /etc/ansible/filebeat-install.yml

 This document contains the following details: 
- Description of the Topology
- Access Policies - ELK Configuration
- Beats in Use 
- Machines Being Monitored 
- How to Use the Ansible Build

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn 
Vulnerable Web Application. Load balancing ensures that the application will be highly available, in addition to 
restricting access to the network. 
- Load Balancers maintain the Availability corner of the CIA Triad. A load Balancer will continue to move traffic to the most available server, even when another is down.
- The advantage of a jumpbox server is it can manage a group of servers from one location. It doesn't require you to log in individually to make updates or corrections.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for 
changes to the vulnerable containers and system logs in a safe and managable way. 
- Filebeat is used for gathering logs and shipping logs so they can be analyzed more easily. 
- Metricbeat is used to collect system-level metrics for certain platforms allowing the administrator a visible performance monitoring.
The configuration details of each machine may be found below.
| Name    | Function | IP Address | Operating System |
----------|----------|------------|------------------| 
|Jump Box | Gateway  | 10.0.0.4   | Linux            |
|Web1     | Container| 10.0.0.7   | Linux            |
|Web2     | Container| 10.0.0.8   | Linux            |
|WebDWVA  | Container| 10.0.0.9   | Linux            |
|Elk      | Container| 10.1.0.4   | Linux            |

### Access Policies
The machines on the internal network are not exposed to the public Internet. 

Only the Load Balancing machine can accept connections from the Internet. 
Access to this machine is only allowed from the following IP addresses: 
- 20.167.40.10 
Machines within the network can only be accessed by RDP via the JumpBox Server. 
- Only my jumpbox has access to my ELK Server 10.0.0.4

A summary of the access policies in place can be found in the table below.
|   Name   | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------| 
| Jump Box |         No          |   10.0.0.1 10.0.0.2  |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is 
advantageous because... 
- Using an ansible play book allows you to quickly configure multiple or new machines without having to put in a ton of code. 

The playbook implements the following tasks: 
- use more memory.
- Install pip
- Install Docker python module
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats

This ELK server is configured to monitor the following machines: 
- 10.0.0.7; 10.0.0.8; 10.0.0.9 
We have installed the following Beats on these machines: 
- Filebeat; Metricbeat 
These Beats allow us to collect the following information from each machine: 
- 'Filebeat' organizes and pushes log data to Elasticsearch for viewing. For example, will log web traffic on a particular web server.
- 'Metricbeat' gathers and pushes system performance analytics to a user friendly dashboard for monitoring.

### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you 
have such a control node provisioned: 

SSH into the control node and follow the steps below: 
- Copy the elk.yml file to the ansible folder.
- Update the elk.yml file to include any services you may want such as filebeat and metricbeat. 
- Run the playbook, and navigate to the included container to check that the installation worked as expected. 

