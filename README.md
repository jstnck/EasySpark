# Running spark on Vagrant, using Ansible

Hello, this is a simple process for setting up a standalone Spark instance on a virtual machine, on your local computer. It uses Vagrant to download and launch the VM, and installs Spark and its dependencies using an Ansible Playbook. You can then access Spark by ssh'ing into the VM, by writing another playbook to run spark jobs from your local machine, and the Spark web interface is accessable by visiting 'localhost:8080' in your browser.

## Software Required

### Virtual Box
- Vagrant requires a virtual machine provider to run. [Virtual Box](https://www.virtualbox.org/) is best for getting started.  

### Vagrant
- Install Vagrant for your manchine [here](https://www.vagrantup.com/downloads.html)
- [Vagrant mini tutorial](https://www.vagrantup.com/intro/getting-started/index.html)

### Ansible
- Install Ansible [here](https://www.ansible.com/)
- Ansible mini tutorial: [Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-use-ansible-to-install-and-set-up-apache-on-ubuntu-18-04)
  
### Spark
- Donwload Spark. for this repo, I used Spark 2.4.5, prebuilt for Hadoop 2.7.

## Instructions

1. Install, VirtualBox, Vagrant, and Ansible
2. Clone this repo to your local machine. 
3. Download the spark archive - in my case the filename is 'spark-2.4.5-bin-hadoop2.7.tgz'. Save the file in 'easySpark/files/
4. tbc...