## Ansible playbook - MEAN stack

This Vagrant and Virtualbox based Ansible playbook sets up a MEAN stack (Mongodb, Node + Express suitable for back-end for Angular SPAs).

### Instructions

* Install VirtualBox and Vagrant (make sure Vagrant is version 1.6.5 or later)
* Install Ansible
* Clone this project to a folder where you keep your VMs
* On the cammand-line in that folder, type `vagrant up`
* The process will take a while, on my 4GB RAM MacBook Pro it took about 10 minutes. A large part of that is the provisioning via Ansible of the MEAN components.
* Associate `http://mean01/` (or any other name you'd like) with local machine IP specified in the Vagrantfile (192.168.46.100 initially) by including the following line in `/etc/hosts`:

    192.168.46.100  mean01

* Within the guest VM box, if you do your work in, say, `/vagrant/dev/project01` then in the VM dir `./dev/project01` you can access the files with your favorite editor or IDE or else edit via ssh remoting.  
* If you create and run a node.js programm on port 3000, you can access it in your browser by pointing it at `http://mean01:3000`.

### Vagrantfile

* Box used: [Ubuntu 14.04 64-bit (Trusty)](https://vagrantcloud.com/ubuntu/boxes/trusty64)
* [Virtualbox settings:](https://www.virtualbox.org/manual/ch08.html#vboxmanage-modifyvm)
 * memory 512
 * IP 192.168.46.100

### Playbook tasks

* Installs build-essential and git packages from Apt.
* MongoDB installation:
 * Imports MongoDB's public GPG key.
 * Adds MongoDB's Apt source.
 * Installs MongoDB
* Node.js installation:
 * Sets up [NodeSource](https://github.com/nodesource/distributions) for Ubuntu.
 * Installs latest version of Node.js.
 * Installs [Grunt](http://gruntjs.com/).
 * Installs [Gulp](http://gulpjs.com/).
