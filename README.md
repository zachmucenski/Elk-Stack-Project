## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Images/Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

Elk-Stack-Project/Ansible/filebeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable, in addition to restricting traffic to the network.
- Load balancers can defend an organization against (DDOS) denial of service attacks. An advantage of using a jumpbox is the ability to use a virtual machine that can manage systems within a security zone.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic .
- Filebeat monitors specified log files.
- Metricbeat records metrics and statistics from the operating system and services that are running on the system

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    |Webserver1| 10.0.0.5   | Linux            |
| Web-2    |Webserver2| 10.0.0.6   | Linux            |
| ELK-VM   |ELK       | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 13.72.115.130


Machines within the network can only be accessed by the Jump Box.
- The Jump Box has access to the ELK VM. The Jump Boxes IP address is 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 13.72.115.130        |
| Web-1    | No                  | 10.0.0.4             |
| Web-2    | No                  | 10.0.0.4             |
| ELK-VM   | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- This allows IT admins to automate daily tasks. This frees them to direct their focus on more important tasks.

The playbook implements the following tasks:
- Install Docker
- Install python3-pip
- Install Docker python module
- Set the vm.max_map_count to 262144
- Download and launch Docker Elk Container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

(Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.5
- Web-2 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filbeat monitors log files that are specified which shows what messages the log files receive. Metricbeat records the metrics andf statistics from the operating system and from other services on the server which allows us to see the CPU and RAM usage on the webservers.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible.
- Update the install-elk.yml file to include the machine that you want to use the playbook on.
- Run the playbook, and navigate to http://[your.VM.IP]:5601/app/kibana to check that the installation worked as expected.


