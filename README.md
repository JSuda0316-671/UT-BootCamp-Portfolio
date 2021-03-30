# UT-BootCamp-Portfolio
This repository contains the following: *Ansible Scripts* *Bash Scripts* &amp; **Projects**

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![https://drive.google.com/file/d/1Ehi8piiANyLZ1d5I4x6hAiy6xBTJwt-M/view?usp=sharing](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the /etc/ansible/pentest.yaml file may be used to install only certain pieces of it, such as Filebeat.

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

Load balancing ensures that the application will be highly available and responsive, in addition to restricting unwanted connectivity to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.
- _TODO: What does Filebeat watch for?_
- _TODO: What does Metricbeat record?_

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function         | IP Address | Operating System |
|----------|------------------|------------|------------------|
| Jump Box | Gateway          | 10.0.0.4   | Ubuntu 18.04-LTS |
| Web-1    | Web Server DVWA  | 10.0.0.8   | Ubuntu 18.04-LTS |
| Web-2    | Web Server DVWA  | 10.0.0.9   | Ubuntu 18.04-LTS |
| Web-3    | Web Server DVWA  | 10.0.0.10  | Ubuntu 18.04-LTS |
| Elk-1    | Elk Server       | 10.1.0.4   | Ubuntu 10.1.0.4  |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 154.6.28.171.
- _TODO: _

Machines within the network can only be accessed by the JumpBox. The JumpBox's IP address is: 10.0.0.4
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Addresses |
|----------------------|---------------------|----------------------|
| Jump Box Provisioner | Yes                 | 154.6.28.171         |
| Web-1                | No                  | 10.0.0.4             |
| Web-2                | No                  | 10.0.0.4             |
| Web-3                | No                  | 10.0.0.4             |
| Elk-1                | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it offers simplicity when it comes to updating and configuring virtual machines at a single point of time. Thus, productivity greatly increases.
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- First, the service 'docker' is installed and its cache is updated. The playbook then verifies that the service is present.
- Next, our playbook procedes onto installing 'pip3',which happens to be a python installer. After the installation is complete, the playbook verifies that the python installer is present.
- Third, our playbook begins installing a docker python module. Just like in the previous steps, our playbook verifies that the python module is present.
- Fourth, the playbook increases our virtual machine's mmap range to 262144. The playbook again verifies that this step has been executed and reloads the systemctl module.
- Fifth, a docker elk container is downloaded. The specific image, 'sebp/elk:761' is downloaded and the playbook verifies that the elk container has been started. The restart policy is then switched to always and the following ports are opened/established: 5601, 9200, and 5044.
- Lastly, the VM and docker are modified to start docker on boot. The playbook's final step is to verify that docker has been set to be enabled on boot.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![https://drive.google.com/file/d/1AeDeHNVcKgT6dFX5Jjhoo1sR6MU2iku2/view?usp=sharing](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- IP Addresses: [10.0.0.8, 10.0.0.9, and 10.0.0.10]

We have installed the following Beats on these machines:
-Filebeat and metricbeat.

These Beats allow us to collect the following information from each machine:
- Metricbeat collects and displays system and service logs. These logs allows us to monitor our server's performance as the services that are running on them.
- Filebeat acts as a lightweight way to forward and centralize logs and files from your entire network.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the /etc/filebeat/filebeat-config.yml file to /etc/ansible/files/filebeat-config.yml.
- Update the file to include IP address of your ELK server.
- Run the playbook, and navigate to the FIlebeat installation page on the ELK Server GUI to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
