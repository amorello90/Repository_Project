## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Azure Virtual Network Diagram](Images/diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

### Load Balancing

Load balancing ensures that the application will be highly available and reliable, in addition to the jump-box restricting access to the network, Load balencers are effectively protecting against distributed denial-of-service (DDoS) attacks through the distribution of treaffic accross all servers within the network.

### ELK Server

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files in Web-1 and Web-2 using the filebeat software and system metrics and statistics using metricbeat software.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Jump-Box-Provisioner | 10.0.0.4   | Linux            |
| Web-1    | webserver| 10.0.0.5   | Linux            |
| Web-2    | webserver| 10.0.0.6   | Linux            |
| ELKserver| webserver| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

- _Home Network_

Machines within the network can only be accessed by Jump-Box-Provisioner.

- _Jump-Box-Provisioner 10.0.0.4_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump-Box-Provisioner | Yes/No              | 23.101.194.28/10.0.0.4  |
| Web-1    | Yes/No              | 10.0.0.5/168.61.66.136  |
| Web-2    | Yes/No              | 10.0.0.6/168.61.66.136  |
| ELKserver| Yes/No              | 10.1.0.4/168.61.43.125  |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows you to configure multiple machines.

The playbook implements the following tasks:

- _Install docker.io_
- _Install python3-pip_
- _Install Docker module_
- _download and launch a docker elk container_

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Docker screenshot of successfull ELK configuring](Images/docker_ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines: 

- _Web-1 (10.0.0.5) & Web-2 (10.0.0.6)_

We have installed the following Beats on these machines:

- _Filebeat & Metricbeat._

These Beats allow us to collect the following information from each machine:

- _Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing, while metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server. An example of filebeat would be anytime a log file changes and an example of metricbeat would be a CPU._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- _Copy the install-elk.yml file to /etc/ansible/install-elk.yml._

- _Update the /etc/ansible/hosts file to include the groups and specify them with brackets, i.e. [Elk], and the Elk-Server IP address, i.e. 10.1.0.4 followed by ansible_python_interpreter=usr/bin/python3._

- Run the playbook, and navigate to http://168.61.43.125:5601/app/kibana#/home to check that the installation worked as expected.

- _The file for the playbook used is install-elk.yml. You would then copy the file to /etc/ansible/install-elk.yml_

- _The file you would need to update to make Ansible run the playbook on a specific machine is /etc/ansible/hosts. To specifiy which machine to install the ELK server on, you can simply specify the group with brackets._

- _To verify if your metricbeat worked, navigate to 168.61.43.125:5601_

_Use these commands to download the repo, download the playbook, update the files, git commands/push repo, list/start/run ansible conatiner, and run the playbook._

### Download Repo
- git clone https://github.com/your-username/yourlink.git

### Download the Playbook
- `ansible-playbook playbook.yml`

### Git commands & Push Repo

- To add files
- `git add .`

- Add single file
- `git add <filename>`

- To confirm commit
- `git commit -m "Commit message"`

- Check status of repository
- `git status`

- Finalize the sync
- `git push`

- Git Update
- `git pull` 

- Push commits to Repo
- `git push origin --set-upstream <-branch->`

### List, Start and Run Ansible Container
- To list containers
- `sudo docker container list -a`

- Start ansible container
- `sudo docker start [container name]`

- Run ansible container
- `sudo docker attach [container name]`

### Run the Playbook
- `ansible-playbook install-elk.yml`