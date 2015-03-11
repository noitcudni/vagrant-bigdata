# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  Vagrant.require_version ">= 1.4.3"

  config.ssh.forward_agent = true

  config.vm.define :bdcoe do | bdcoe |
    bdcoe.vm.box = "chef/centos-6.5"

    #if Vagrant.has_plugin? ("vagrant-proxconf")
      #bdcoe.proxy.http = 
      #bdcoe.proxy.https = 
      #bdcoe.proxy.no_proxy = "localhost, 127.0.0.1"
    #end
    
    # Create a private network
    bdcoe.vm.network :private_network, ip: "192.168.5.22"
    #bdcoe.vm.network :forwarded_port, guest:22, host: 2222, id: "ssh", disabled: true
    bdcoe.vm.network :forwarded_port, guest:22, host: 2230, auto_correct: true
    bdcoe.vm.hostname = "bdcoe.vagrant-local.com"

    #VirtualBox provider
    bdcoe.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      vb.name = "bdcoe"
      vb.customize ["modifyvm", :id, "--memory", "7168"]
      # vb.customize ["modifyvm", :id, "--cpus", "2"]
    end

  end
end

