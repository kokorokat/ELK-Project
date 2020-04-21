## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Diagram](https://github.com/kokorokat/ELK-Project/tree/master/Images)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ![Filebeat-Playbook](https://github.com/kokorokat/ELK-Project/blob/master/filebeat-playbook.ymlfile) file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly distributed, in addition to restricting traffic to the network.
The primary function of a load balancer is to spread workloads across multiple servers to prevent overloading servers, optimize productivity, and maximize uptime. Load balancers also add resiliency by rerouting live traffic from one server to another if a server falls prey to DDoS attacks or otherwise becomes unavailable. In this way, load balancers help to eliminate single points of failure, reduce the attack surface, and make it harder to exhaust resources and saturate links.

The advantage of the jump box is the ability to access devices in separate security zones, like managing a host in a DMZ from trusted networks or computers. The ability to strictly prohibit SSH log in using password, as well as making sure than only strong keys are used is another security feature and an advantage of the jump box.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes in data and system logs.

Filebeat collects data about the file system. It logs information about the files system, including which files have changed and when. It is often used to collect log files from very specific files, those generated by Apache, the Nginx web server, MySQL databases and Microsoft Azure Tools.

Metricbeat records machine metrics, such as uptime.

The configuration details of each machine may be found below.

| Name       | Function     | IP Address | Operating System |
|------------|--------------|------------|------------------|
| Jump Box   | Gateway      | 10.0.0.4   | Linux            |
| DVWA-VM1   | Load Balancer| 10.0.0.7   | Linux            |
| DVWA-VM2   | Load Balancer| 10.0.0.8   | Linux            |
| ELK-Server | ELK Stack    | 10.0.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 10.0.0.4  and 13.82.213.38


Machines within the network can only be accessed by SSH key.
I allowed access from DVWA-VM1 machine to the ELK VM - 10.0.0.7

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses    |
|------------|---------------------|-------------------------|
| Jump Box   | Yes                 | 10.0.0.4 13.82.213.38   |
| DVWA-VM1   | No                  | 10.0.0.7                |
| DVWA-VM2   | No                  | 10.0.0.8                |
| ELK-Server | Yes                 | 10.0.0.6 104.211.41.210 |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because by configuring the security details on the control machine and run the associated playbook, all the remote hosts will automatically be updated with those details. That means you won’t need to monitor each machine for security compliance continually manually. And for extra security, an admin’s user ID and password aren’t retrievable in plain text on Ansible.

The playbook implements the following tasks:

1. Install Docker and verify you are in your Ansible container.
2. Create a new playbook: touch /etc/ansible/install-elk.yml.
3. Ensure that the header of the playbook must specify elkservers as the target hosts.
4. Write tasks that do the following:
- Runs the following command through the shell: sysctl -w vm.max_map_count=262144
- Installs the following packages:
docker.io: The Docker engine, used for running containers.
python-pip: Package used to install Python software.
docker: Python client for Docker. Required by ELK.
- Downloads the Docker container called sebp/elk.
- Configures the container to start with the following port mappings:
5601:5601
9200:9200
5044:5044
-Starts the container.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

