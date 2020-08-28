# Ansible_ELK
- Create ELK server with Ansible at the helm
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Network Diagram path: https://github.comGitHub\AnElk\Ansible_ELK/13%20Elk-Stack%20ProjectGHR.png

If you are working from a Remote PC outside of Azure Labs Portal and like to verify your Development progress ensure you update your Red_Team_SG security group rule and include your "changed" dynamic IP adrres before accessing remotly.

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above.
[install-elk.yml]

Alternatively, select portions of the Ansible 'install-elk.yml' file may be used to install only certain pieces of it, such as Filebeat.

[filebeat-playbook.yml]

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration @ tor-tor-cyber-pt-05-2020-u-c\Unit-13-Elk-Stack-Project/ELK_parameters.json
- ELK Configuration @tor-tor-cyber-pt-05-2020-u-c\Unit-13-Elk-Stack-Project/ELK_template.json
- Beats in Use @ - [filebeat-configuration.yml] @ tor-tor-cyber-pt-05-2020-u-c\Unit-13-Elk-Stack-Project
- Beats in use @ - [[filebeat-playbook.yml] @ tor-tor-cyber-pt-05-2020-u-c\Unit-13-Elk-Stack-Project]
- Help @ (https://www.elastic.co/beats/filebeat)
- Machines Being Monitored: Web1 = Subscription ID db9fec09-5dde-4382-b55f-f8353d6ee82d
- Machines Being Monitored: Web2 = Subscription ID db9fec09-5dde-4382-b55f-f8353d6ee82d
- How to Use the Ansible Build Refer to the [official Ansible documentation](https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html)

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA.

Load balancing ensures that the webserving applications on both Webservers will be will be highly secure and efficient in "pushing" site content. In addition, allowing only one source of access "Public IP infrastucture" will restrict external accees to the internal network/ the "Stack". The DVWA Vulnerable Web Application will be accessed by a single Public Address and further development will buildout the remaining customized Webserver offereings.

Integrating an ELK server allows users to easily monitor the vulnerablity of the attached Webserver-VMs for changes to the network configuration and/or system access requests and of course traffic load.
Filebeat an important component watches for events and controls the delivery of the configured outputs and ensure no data loss. Filebeat has the ablity to achieve this behavior because it stores the delivery state of each event in a registry file.

- Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the servers so we installed Metricbeat in order to periodically collect metrics from the operating system and from services running on our Web1 and Web2 Apache servers. Along with collecting metrics and statistics output from the Web servers we can collect "Custom" specified dada from MySql, and even such as Elasticsearch or Logstash.

 The configuration details of each machine can be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux (18.04)    |
| Web1     | Webserver| 10.0.0.5   | Linux (S_B1ms)   |
| Web2     | Webserver| 10.0.0.7   | Linux (S_B1ms)   |
| ELK-VM   | ELKserver| 10.1.0.4   | Linux (S_D2s_v3) |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Load Balencer machine can accept connections from the Internet. Access to this machine is only allowed from the following public IP addresses: Loadbalancer "Webservers": Https/Http 52.229.117.207

Machines within the network can only be accessed by Jumpbox.
- the ELK-server can be accessed by Jump-box "Ansible" by internal IP address: 10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes ssh             | 52.235.56.92         |
| Web1     | No                  | 10.0.0.5             |
| Web2     | No                  | 10.0.0.7             |
| ELK      | No                  | 10.1.0.4             |
| LB       | Yes                 | 52.229.117.207       |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it effectianly produces known configurations and limiting configuration errors through "human error".

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web1 @ IP address 10.0.0.5
- Web2 @ IP address 10.0.0.7

We have installed the following Beats on these machines:
- Web1_VM
- Web2_VM
See the Filebeat confiuragtion file here: GitHub\tor-tor-cyber-pt-05-2020-u-c\Ansible\filebeat-configuration.yml

The File beat installation was performed by playbook: GitHub\tor-tor-cyber-pt-05-2020-u-c\Ansible\filebeat-playbook.yml

These Beats allow us to collect the following information from each machine:
- Filebeat is often used to collect log files from very specific files, such as logs generated by Apache, Microsoft Azure tools, the Nginx web server, or MySQl databases. Today you will be using it to monitor the Apache server and MySQL database logs generated by DVWA.
Example `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.yml file to Ansible container or the Jumpbox.
- Update the YAML file to include the service or features you wan to install on the ELK server.
- Run the playbook, and navigate to ELK server to check that the installation worked as expected.
- Ensue your filebeat installations completed on each of the WEB-VMs by checking for Log data with either ElectsicStack or Kibana. 

- URL to navigate in order to check that the ELK server is running: http://52.138.24.255:5601/app/kibana
- NOTE: Inoder to access the Kibana interface you will need to ensure your "Dynamic IP address has been updated in the Kibana access      - rules. This is a Development Access Issue if you donot have a Static IP.
- See "Snapshot": https://github.com/projectname/folder/Issues_Capture_DynamicIP.PNG

- Added Guidance, See Command Line TXT documents for common syntax and installation issues: https://GitHub\AnElk\Ansible_ELK\Command Line - Issues
### END OF FILE