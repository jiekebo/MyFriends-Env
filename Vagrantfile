Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.network "forwarded_port", guest: 5000, host: 5000
  
  config.vm.synced_folder "./salt/root/", "/srv/salt/"
  config.vm.synced_folder "./salt/pillar/", "/srv/pillar/"
  config.vm.synced_folder "../myfriends/", "/code/"

  config.vm.provision :salt do |salt|
    salt.minion_config = "salt/minion"
    salt.run_highstate = true
    salt.verbose = true
    salt.colorize = true
    salt.install_type = "git"
    salt.install_args = "v2014.1.10"
  end
 
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

end
