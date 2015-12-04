# homestead
### Included Software
* ubuntu/trusty64 14.04

### Setup
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
note: If you want to use the custom local box or other box from this site(https://atlas.hashicorp.com/boxes/search).
<pre>$ grep "vm.box"  ./scripts/homestead.rb -A1 -B1
    # Configure The Box
    config.vm.box = settings["box"] ||= "ubuntu/trusty64"
    config.vm.hostname = settings["hostname"] ||= "dev.example.com"</pre>
* Configuring Shared Folders</br>
The folders property of the ~/.homestead/Homestead.yaml file lists all of the folders you wish to share with your Homestead environment. As files within these folders are changed, they will be kept in sync between your local machine and the Homestead environment. You may configure as many shared folders as necessary:
<pre>folders:
     \- map: ~/Code
        to: /home/vagrant/Code
</pre>

### Daily Usage
You can SSH into your virtual machine by issuing the vagrant ssh terminal command from your Homestead directory.</br>
But, since you will probably need to SSH into your Homestead machine frequently, consider creating an "alias" on your host machine to quickly SSH into the Homestead box. </br>
Once you create this alias, you can simply use the "vm" command to SSH into your Homestead machine from anywhere on your system:
<pre>alias vm="ssh vagrant@127.0.0.1 -p 2222"</pre>

