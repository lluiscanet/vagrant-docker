vagrant-docker
==============

This project will allow you to programmatically create a Virtual Machine (VM) using [Vagrant](http://www.vagrantup.com/) with [Docker](http://www.docker.io/) pre-installed.
You can mount any local folder containing your docker files or any of the docker projects that you can find in [Lluis Canet Github](https://github.com/lluiscanet?tab=repositories) and start your docker instances inside your VM.

####Requirements
Before you make use of this project. You need to make sure that:
* Your host machine has at least 1GByte of RAM memory free for you new VM to use.
* You have [VirtualBox](https://www.virtualbox.org). If you don't have it installed, you can download the [installation packaage](https://www.virtualbox.org/wiki/Downloads) that applies to your Host OS
* You have [Vagrant](http://www.vagrantup.com/) installed in your host machine. If you don't have it isntalled, you can download the [installation packaage](http://www.vagrantup.com/downloads.html) that applies to your Host OS

####Mounting folders from your Host OS to your VM

To mount a shared folder with the host OS, uncomment the line in Vagrantfile
```config.vm.synced_folder "~/Documents/workspace", "/vagrant-data"```
and replace the "~Documents/workspace" with the folder that you whish to mount.
After any change to you Vagrantfile, you should destroy the VM with ```vagrant destroy``` and rebuild it with ```vagrant up```.

####Port forwarding
If you want to forward some ports from your VM to your Host machine, uncomment in the Vagrantfile
```config.vm.network "forwarded_port", guest: 80, host: 8080``` and replace the guest port and host port with the ones you want to forward.:
After any change to you Vagrantfile, you should destroy the VM with ```vagrant destroy``` and rebuild it with ```vagrant up```.

####Setting Up your VM for the first time

Get and start your virtual box for the first time:

```
vagrant box add "ubuntu_12.04.3_docker" https://oss-binaries.phusionpassenger.com/vagrant/boxes/ubuntu-12.04.3-amd64-vbox.box
vagrant up
```

The virtual box started will contain Docker and Git so that you can clone any docker file from a Git repository and run it in your VM.

#### Accessing, Stopping and Restarting your VM
To ssh into your new VM
```vagrant shh```

To stop your VM but keep your current running state
```vagrant suspend```

To stop your VM by greacefully shutting down your guest OS
```vagrant halt```

To stop your VM and destroy all its files (irreversible)
```vagrant destroy```

To restart your VM after shutting down with any of the options above
```vagrant up``` 

