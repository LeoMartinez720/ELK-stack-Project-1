## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(LeoMartinez720/ELK-stack-Project-1)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire 
deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such 
as Filebeat.

  - _TODO: Enter the playbook file._ filebeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly secure and avaiable, in addition to restricting access to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box? 

Load balancers protect availablity to a network by splitting up the web traffic to the servers as to not overload them with too many 
requests to one server. The advantage of having a jumpbox connected to your network is you have one way access into the network to test
vulternabilties on the network without any worry of interuption. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____metrics and system logs.
- _TODO: What does Filebeat watch for?_ Filebeat watches for changes on log files or locations that are set by you for it to watch.
- _TODO: What does Metricbeat record?_ Metricbeat gathers metrics from the operating system and from services running on the server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jbox-LM  | Gateway  | 10.0.0.4   | Linux            |
| Web1     | DVWA VM1 | 10.0.0.7   | Linux            |
| Web2     | DVWA VM2 | 10.0.0.8   | Linux            |
| ELK-VM   | ELK VM   | 20.124.114.139 | Linux        |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Web2 machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: List of Whitelisted IPs: 20.124.114.139, 52.165.188.141, 10.0.0.4 

Machines within the network can only be accessed by Web2.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_ 10.0.0.8
A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 6.137.139.57         |
| Web1 & Web2 | yes              | public               |
| ELK-VM   | No                  | 10.0.0.8             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_ The main advantage to automating with Ansible is to make it quick and easy for 
the user to install the applications via scripting.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install docker.io
- install pip3
- install docker python module
- use more memory
- download and launnch a docker elk container
- enable service docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)
( the first container, cool_zhukovsky, is running Ansible and ELK)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_ 10.0.0.7 and 10.0.0.8

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_ Filebeat and Metricbeat were successfully installed.

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., 
`Winlogbeat` collects Windows logs, which we use to track user logon events, etc._ 

Filebeat collects and logs data that you specify for it to collect. Once it collects the data it displays it on the output you set it up on. When using Filebeat
I expect to see requests made on the server and what the output was when the request is finalized.

Metricbeat collects metrics from the operating system from the services running on the system. Metricbeat take the statisics and displays them on the output
you specify for it to use. When using Metricbeat I expect to see different types of usages on the system such as memory usage, inbound traffic data transfers, 
outbound data transfers, CPU usage and disk space used.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node 
provisioned: 

SSH into the control node and follow the steps below:
- Copy the Filebeat/Metricbeat YML file to Filebeat/Metricbeat Config File.
- Update the Config file to include...
- Run the playbook, and navigate to the installation pages to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ The playbook file is the one used to install the applications and copy data to another file. The playbook
is not copied, the config file is copied to the Ansible container installed on the WebVMs where Filebeat and Metricbeat are installed.

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK 
server on versus which to install Filebeat on?_ The file that is updated to run Ansible on is the Hosts file in the /etc/ansible/ directory. The config files
are changed to include the ip addresses of the machines used to run ELK and the beats based on the output within the config file.

- _Which URL do you navigate to in order to check that the ELK server is running? http://[your.VM.IP]:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
