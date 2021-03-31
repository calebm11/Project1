# Project1
Week 13 Project for Cybersecurity Class

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagrams/Diagram 2.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .yml file may be used to install only certain pieces of it, such as Filebeat.

  install-elk.yml
  pentest.yml
  filebeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system statistics.

The configuration details of each machine may be found below.


| Name                | Function        | IP Address | Operating System |
|---------------------|-----------------|------------|------------------|
| Jump-Box-Provisioner| Gateway         | 10.0.0.4   | Linux            |
| Web-1               | DVWA Container  | 10.0.0.7   | Linux            |
| Web-2               | DVWA Container  | 10.0.0.8   | Linux            |
| ELK-SERVER          | ELK log reciver | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 71.18.112.236

Machines within the network can only be accessed by Jump-Box-Provisioner at 23.96.115.8

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.1 10.0.0.2    |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because
this configuration can be automated and quickly deployed to any new machine we add to the network using a playbook. 

The playbook implements the following tasks:
*Install Docker
*Install python
*Instruct system to use more memory
*download and launch elk container
*enble docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
Images/docker_ps_output.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web-1 at 10.0.0.7
Web-2 at 10.0.0.8

We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
- Filebeat is used to forward and centralize log data. It is used to monitor the log data and locations.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible/
- Update the /etc/ansible/hosts file to add "[local IP] ansible_python_interpreter=/usr/bin/python3" to the [elk] group
- Run the playbook, and navigate to "HTTPS://[public ip]:5601/kibana" to check that the installation worked as expected.
