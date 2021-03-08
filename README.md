## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/Saaphire999/Elk-Stack-Project/blob/main/Network%20Diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

  -Playbook file: /etc/ansible/elkplaybook.yml

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
- Load balancers protect systems from DDoS attacks by shift attack traffic. The advantage of a jump box is to restrict access to the networks.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system log.
-Filebeat watches for files in the system that has been changed and when.
-Metricbeat measure statistic about data collected and ships them to a specific output.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table. 

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.5   | Linux            |
| Web- 1   |  Server  | 10.0.0.6   | Linux            |
| Web- 2   | Server   | 10.0.0.7   | Linux            |
|Elk server| Server   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Elk machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 23.118.88.127

Machines within the network can only be accessed by Jumpbox.
- Jumpbox IP address 10.0.0.5

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 23.118.88.127        | 
| Web - 1  | No                  |   10.0.0.6           |
| Web - 1  | No                  |   10.0.0.6           |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

- The main advantage of automating configuration with Ansible is it is easy to put commands for multiple servers. It saves time and causes less room for error.

The playbook implements the following tasks:
 
•	Install Python pip3
•	Install Docker python module
•	Use more memory
•	Download and launch a docker elk container
•	Enable service docker on boot
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![image](https://user-images.githubusercontent.com/80162971/110356472-4c1d1480-8008-11eb-8ff4-699323f5c4c2.png)


### Target Machines & Beats

This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.6 Web-2 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects the logs and analyze the changes done to a system.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to ansible.
- Update the playbook file to include...
- Run the playbook and navigate to Kibana to check that the installation worked as expected.

Answer the following questions to fill in the blanks:_
- Which file is the playbook? Where do you copy it? _/etc/ansible/file/filebeat-config.yml

- _Which file do you update to make Ansible run the playbook on a specific machine? Host file How do I specify which machine to install the ELK server on versus which to install Filebeat on?_Elk server is on elk server, filebeat is installed on web vm.

- Navigate to 104.42.154.252:5601/app/kibana
 in order to check that the ELK server is running.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._ansible-playbook filebeat-playbook.yml
