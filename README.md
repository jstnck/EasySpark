# Running Spark on Vagrant, using Ansible

Hello, this is a simple process for setting up a standalone Spark instance on a virtual machine, on your local computer. It uses Vagrant to download and launch the VM, and installs Spark and its dependencies using an Ansible Playbook. You can then access Spark by ssh'ing into the VM, by writing another playbook to run spark jobs from your local machine, and the Spark web interface is accessable by visiting 'localhost:8080' in your browser.

## Software Required

### Virtual Box
- Vagrant requires a virtual machine provider to run. [Virtual Box](https://www.virtualbox.org/) is best for getting started.  

### Vagrant
- Install Vagrant for your manchine [here](https://www.vagrantup.com/downloads.html)
- Optional: [Vagrant mini tutorial](https://www.vagrantup.com/intro/getting-started/index.html)

### Ansible
- Install Ansible using thie guide [here](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
- Optional: [Ansible mini tutorial](https://www.digitalocean.com/community/tutorials/how-to-use-ansible-to-install-and-set-up-apache-on-ubuntu-18-04) - you can follow these instructions using the vagrant VM you just set up as the Ansible Host
  
### Spark
- Donwload [Spark](https://spark.apache.org/downloads.html). For this repo, I used Spark 2.4.5, prebuilt for Hadoop 2.7.

## Instructions

1. Install, VirtualBox, Vagrant, and Ansible.
2. Clone this repo to your local machine. 
3. Download the Spark archive - in my case the filename is 'spark-2.4.5-bin-hadoop2.7.tgz'. Save the file in 'easySpark/files/

    3.1. If you download another ditro of spark, you need to modify playbook.yml. At the beginning of the playbook, change the 'spark_dist' variable to match the filename (minus the .tgz suffix)
4. Run 'vagrant up' from your command line. This will download your VM OS (the hasicorp dist of ubuntu 18.04), and start your VM. 
    
    4.1. From the output, you will see vagrant set up the virutal machine, then call the ansible playbook to provision the machine. Hopefully, the playbook will run without error. It may take a while as it updates all apt packages and installs java, which is required to run Spark.
5. Check that its running with 'vagrant status'.


Thats it! The Spark files should be located at /home/vagrant/spark, and a linked to the directory /usr/local/spark. This /usr directory is in the VM's env variable list at $SPARK_HOME.

## Accessing Spark

 You can access the machine directly by running 'vagrant ssh'. If you want to use ssh to access the machine without 'vagrant ssh', you can use ssh normally:
- the user is 'vagrant'
- the ip of the VM is 192.168.10.101 (this can be modified in the Vagrantfile)
- the ssh private key is at "easySpark/.vagrant/machines/default/virtualbox/private_key" 
- the port is 2222

To access the Spark cli, you can ssh into your VM, and run '$SPARK_HOME/bin/spark-shell'

To start a Spark master instance, you can run '$SPARK_HOME/sbin/start-master.sh'. To stop, there is a 'stop-master.sh' script.
- The Spark web interface can be found by using your browser and visiting 'localhost:8080'

### next
I'm attempting to configure a spark cluster on 3 raspberry pis - you can check out that project (work on progress) at my RpiclusteR repo.