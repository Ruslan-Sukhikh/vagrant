ENV['VAGRANT_SERVER_URL'] = 'http://vagrant-cloud.uncomp.com'
Vagrant.configure("2") do |config|
 
  config.vm.box = "essay/ubuntu"
  config.vm.network :private_network, ip: "192.168.56.101"
  config.ssh.forward_agent = true
  config.vm.hostname = "devbox.local"
 
  config.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 2048]
  end
 
  config.vm.synced_folder "", "/var/www/html", group: "www", owner: "www",  create: "true"
#  config.vm.box_url = "https://atlas.hashicorp.com/Jeyraboy/boxes/ubuntu-staging-1.2.box"
 
  config.vm.network "forwarded_port", guest: 80, host: 81
  config.vm.network "forwarded_port", guest: 443, host: 443
  
#  config.vm.provision :puppet do |puppet|
#     puppet.hiera_config_path = "hiera.yaml"
#     puppet.manifests_path = "environments/staging/manifests"
#     puppet.manifest_file = "default.pp"
#     puppet.module_path  = "environments/staging/modules"
#   end
end
