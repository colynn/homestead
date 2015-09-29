# homestead
###Included Software
* ubuntu/trusty64 14.04

### Daily Usage
You can SSH into your virtual machine by issuing the vagrant ssh terminal command from your Homestead directory.</br>
But, since you will probably need to SSH into your Homestead machine frequently, consider creating an "alias" on your host machine to quickly SSH into the Homestead box. </br>
Once you create this alias, you can simply use the "vm" command to SSH into your Homestead machine from anywhere on your system:
<pre>alias vm="ssh vagrant@127.0.0.1 -p 2222"</pre>
