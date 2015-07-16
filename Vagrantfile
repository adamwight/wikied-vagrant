# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "debian/jessie64"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  config.vm.provision :shell, inline: 'apt-get install -y puppet'

  config.vm.provision :puppet do |puppet|
    puppet.hiera_config_path = "hiera.yaml"
    puppet.module_path = "modules"
    puppet.facter = { environment: 'development' }

    puppet.options << '--debug' if ENV.include?('DEBUG')
  end
end