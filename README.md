# VagrantTuts

<h2>Vagrant Tutorials</h2>
<b>1) Reguirements</b><br>
Virtual box - https://www.virtualbox.org/wiki/Downloads <br>
Vagrant - https://www.vagrantup.com/downloads.html <br>
(Choose appropriate package for your OS. Select CentOS version for OpenSuse)
Install both softwares.<br>
After installation check whether they both are installed by looking the version.<br>
```shell
$ vboxmanage --version
5.0.18_SUSEr106667
$ vagrant --version
Vagrant 1.8.5

```
<b>2) Creating the first box</b><br>
Create a folder, Run the command inside the folder.<br>
```shell
$ mkdir vagrantbox
$ cd vagrantbox
$ vagrant init hashicorp/precise64
```
After init, There is a configuration file ```Vagrantfile``` created inside the folder. See the file using ```cat Vagrantfile```. Dont edit anything now. Next, run <br>
```$ vagrant up```

It may take some time depending upon your net. It is actually downloading ```Ubuntu 14.04.5 LTS 64 box```from vagrant.<br>
After finishing Downloads & all the process., a new box will be added to Virtual Box.<br>
So we created our first box.<br><br>
<b>3) Entering to VM</b><br>
From same folder, run
```
$ vagrant ssh
```
Now, you will be successfully entered into the box. You can execute various commands inside the box.<br>
* Shut down the box<br>
```
$ vagrant halt
```
* Power on the box<br>
```shell
$ vagrant up
```
* Restart the box<br>
```shell
$ vagrant reload
```
* Destroy the box<br>
```shell
$ vagrant destroy
```
Note: This will not remove the box. we can start the box again using ```vagrant up``` <br>

* Removing the Box
```shell
vagrant box remove <box name>
$ vagrant box remove hashicorp/precise64
```
<b>4) Add the box </b><br>
After removing the box, You need to add the box again.<br>
Use ```vagrant up```. This will download the file again using ```Vagrantfile```.<br>
If there is no Vagrantfile, You need to use ```vagrant init``` & ```vagrant box add```<br>
```vagrant box add``` is another way of adding box.
```shell
$ vagrant init
$ vagrant box add hashicorp/precise64
```
This will show multiple providers. We are using virtual box here. So enter 2.
```shell
This box can work with multiple providers! The providers that it
can work with are listed below. Please review the list and choose
the provider you will be working with.

1) hyperv
2) virtualbox
3) vmware_fusion

Enter your choice: 2
```
Before using ```vagrant up```, You need to edit the ```Vagrantfile```
Find ```config.vm.box = "base"``` in the file and remove ```base``` with the box name```config.vm.box = "hashicorp/precise64"``` and run<br>
```shell 
$ vagrant up
```
<b>5) File sharing with vagrant box </b><br>
The current folder ```vagrantbox``` in the host system & ```/vagrant``` in the box is synced.<br>
Goto your folder and create some files.<br>
```shell
$ cd vagrantbox
$ ls
Vagrantfile
$ touch 1 2 3
$ ls
1  2  3  Vagrantfile
```
Now ssh into box & check the folder.
```shell
$ vagrant ssh
vagrant@precise64:~$ ls /vagrant/
1  2  3  Vagrantfile
```

Create some files and check from the host system<br>
```shell
vagrant@precise64:~$ cd /vagrant/
vagrant@precise64:~$ touch 4 5 6
vagrant@precise64:~$ ls 
1  2  3  4  5  6  Vagrantfile
vagrant@precise64:~$ exit
$ ls
$ 1  2  3  4  5  6  Vagrantfile
```
