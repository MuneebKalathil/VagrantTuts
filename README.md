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
From same folder, run<br>
```shell
$ vagrant ssh
```<br>
Now, you will be successfully entered into the box. You can execute various commands inside the box.<br>
* Shut down the box<br>
```shell
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


