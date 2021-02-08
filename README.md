# Azure
Azure Cloud Environment

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[network_diagram](Images/network_diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the relevant playbook file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the operating system and system files.

The configuration details of each machine may be found below.

| Name       | Function  | IP Address | Operating System |
|------------|-----------|------------|------------------|
| jump-box   | Gateway   | 10.0.0.4   | Linux            |
| web-1      | vm        | 10.0.0.5   | Linux            |
| web-2      | vm        | 10.0.0.6   | Linux            |
| web-3      | vm        | 10.0.0.7   | Linux            |
| elk-server | elk sever | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump-box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
144.48.36.84

Machines within the network can only be accessed by 10.0.0.4.

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses |
|------------|---------------------|----------------------|
| jump-box   | yes                 | 10.0.0.1 10.0.0.2    |
| web-1      | no                  | 10.0.0.4             |
| web-2      | no                  | 10.0.0.4             |
| web-3      | no                  | 10.0.0.4             |
| elk-server | no                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous as it reduces errors and can be used to configure mulitple machines in one go.

The playbook implements the following tasks:
- install docker.io
- install python3-pip
- install docker
- increase virtual memory
- download and launch docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
[docker_ps_output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5, 10.0.0.6, 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
- Filebeats monitors log files looking for new changes. It sends the new data to libbeat.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk.yml playbook file to /etc/ansible/files/.
- Update the hosts file to include IP address of machines to configure (under a suitable heading, for example: [webservers])
- Run the playbook, and navigate to 23.99.8.109:5601/app/kibana to check that the installation worked as expected.
