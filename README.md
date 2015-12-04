# homestead
### Included Software
* ubuntu/trusty64 14.04

### Installation & Configuring 
* First Steps</br>
Before launching your Homestead environment, you must install VirtualBox 5.x or VMWare as well as Vagrant. All of these software packages provide easy-to-use visual installers for all popular operating systems.</br>
To use the VMware provider, you will need to purchase both VMware Fusion / Workstation and the VMware Vagrant plug-in. VMware provides much faster shared folder performance out of the box.


* Checkout and Init 
<pre>$ git clone https://github.com/colynn/homestead.git homestead
$ cd homestead
$ bash init.sh</pre>

* Setting Your Provider
The provider key in your ~/.homestead/Homestead.yaml file </br>
indicates which Vagrant provider should be used: virtualbox, vmware_fusion, or vmware_workstation. </br>
You may set this to whichever provider you prefer:
<pre>provider: virtualbox</pre>

* Setting Your SSH Key
<pre>$ ssh-keygen -t rsa </pre>

* Defind Your Box Name</br>
<pre>$ grep "vm.box"  ./scripts/homestead.rb -A1 -B1
    # Configure The Box
    config.vm.box = settings["box"] ||= "ubuntu/trusty64"
    config.vm.hostname = settings["hostname"] ||= "dev.example.com"</pre>
Note: If you want to use the custom local box(can download from http://www.vagrantbox.es/) or other virtualbox from https://atlas.hashicorp.com/boxes/search, you can change the setting of 'config.vm.box', as you saw,the default value is 'ubuntu/trusty64'.</br>
And you may use this command to add the local box.
<pre>vagrant box add [customer-box-name] [the local virtualbox file]</pre>    
* Configuring Shared Folders</br>
The folders property of the ~/.homestead/Homestead.yaml file lists all of the folders you wish to share with your Homestead environment. As files within these folders are changed, they will be kept in sync between your local machine and the Homestead environment. You may configure as many shared folders as necessary:
<pre>folders:
     \- map: ~/Code
        to: /home/vagrant/Code
</pre>

### Launching The Vagrant Box

Once you have edited the ~/.homestead/Homestead.yaml to your liking, run the vagrant up command from your Homestead directory. Vagrant will boot the virtual machine and automatically configure your shared folders and Nginx sites.

To destroy the machine, you may use the vagrant destroy --force command.
### Daily Usage
You can SSH into your virtual machine by issuing the vagrant ssh terminal command from your Homestead directory.</br>
But, since you will probably need to SSH into your Homestead machine frequently, consider creating an "alias" on your host machine to quickly SSH into the Homestead box. </br>
Once you create this alias, you can simply use the "vm" command to SSH into your Homestead machine from anywhere on your system:
<pre>alias vm="ssh vagrant@127.0.0.1 -p 2222"</pre>

