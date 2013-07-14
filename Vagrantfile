# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.omnibus.chef_version = :latest
  config.vm.box = "ubuntu1204"
  config.vm.network :private_network, ip: "10.42.0.2"

  # config.vm.network :public_network

  config.vm.synced_folder "./communitask", "/home/vagrant/communitask"

  config.vm.provider :virtualbox do |vb|
    # Uncomment to boot with GUI
    # vb.gui = true
    vb.customize ["modifyvm", :id, "--memory", "512"]
  end
 
  config.vm.provision :chef_solo do |chef|
    chef.json = {
      "environment" => "development",
      "base" => {
        "user" => {
          "name" => "vagrant",
          "group" => "vagrant",
          "home" => "/home/vagrant"
        }
      }
    }
    chef.cookbooks_path = "./cookbooks"
    # chef.add_recipe "_base"
  end
end
