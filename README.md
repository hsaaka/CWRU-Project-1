# CWRU-Project-1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

**Note**: The following image link needs to be updated. Replace `diagram_filename.png` with the name of your diagram image file.  

https://drive.google.com/file/d/17wpMNhdLkAogctS3hpqovRkonU9r5aWo/view?usp=sharing

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._ https://drive.google.com/file/d/13S7mxgA0opINO9Ee20ki8Jl60jcBbHaa/view?usp=sharing

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

- Load balancing protects a system from being overwhelmed by traffic by distributing it between webservers rather than having it all concentrated on one machine.
This has the added benefit of preventing a network from being taken down DDOS attacks since traffic can be rerouted to another server. 
- The main benefit of a Jumpbox is that it acts as a staging point to access the webservers as an Ansible Control node rather than directly connecting to them
externally


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the application and system logs.
- _TODO: What does Filebeat watch for?_  Filebeat monitors Elastic search log files and makes them visible for analysis on Kibana.
- _TODO: What does Metricbeat record?_ Metricbeat records statistics and other metrics as they pertain to changes in the system as they are created.
They are then collected and transferred to Elastic Search or Logstash

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function     | IP Address | Operating System |
|----------|--------------|------------|------------------|
| Jump Box | Gateway      | 10.0.0.4   | Linux            |
| Web 1    | Webserver    | 10.0.0.5   | Linux            |
| Web 2    | Webserver    | 10.0.0.7   | Linux            |
| Web 3    | Webserver    | 10.0.0.8   | Linux            |
| Elk      | ELK Stack    | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Gateway (Jump-Box provisioner) machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_10.0.0.4, 52.188.160.84

Machines within the network can only be accessed by Ansible.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address? 172.58.83.120 (This changes each session since it is the Workstation ip)

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.4   |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

Automating the process via Ansible allows the ELK configuration to be setup quickly if there was any reason it had to be taken down or shifted to a new 
set of hardware.   Only the IP information would have to be updated.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install Docker
- Configure Ansible Playbook
- Launch Container
- Add data to Kibana
- Download/install Filebeat
- Download/install Metricbeat

- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

**Note**: The following image link needs to be updated. Replace `docker_ps_output.png` with the name of your screenshot image file.  


![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines: Web1, Web2, Web3
- _TODO: List the IP addresses of the machines you are monitoring_
10.0.0.5
10.0.0.7
10.0.0.8

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
Filebeat
Metricbeat


These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

-Filebeat collects logs from Elasticsearch module.  It captures audit log, server logs and other information produced over the network
-Metricbeat collects system metrics from the operating system and services running on the server

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook.yml file to ansible directory.
- Update the hosts file to include the IP for the new ELK VM
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
- Enter "nano /etc/ansible/hosts" to edit and add Elk server to the hosts file in the Ansible's inventory
- Create a new Ansible Playbook entering "touch /etc/ansible/install-elk.yml"
