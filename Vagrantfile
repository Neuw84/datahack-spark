# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.require_version ">= 2.0"

# 
require File.dirname(__FILE__)+"/dependency_manager"
check_plugins ["vagrant-hostmanager"]


## Plugin Validation
##############################################

if Gem::Version.new(::Vagrant::VERSION) < Gem::Version.new('1.5')
  Vagrant.require_plugin('vagrant-hostmanager')
end


Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  
  
  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "ubuntu/xenial64"
  #config.vm.box_version = " v20170427.0.0"
  config.vm.hostname = "spark"

  #  host manager config
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.manage_guest = true

  
  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network 'private_network', ip: '192.168.33.10'
  # zeppelin
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  # spark ui
  config.vm.network "forwarded_port", guest: 4040, host: 4040
  # cassandra 
  config.vm.network "forwarded_port", guest: 9042, host: 9042

  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--cpus", "2"]
    vb.customize ["modifyvm", :id, "--memory", "4096"]
    vb.name = "spark"
  end

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"


  # If true, then any SSH connections made will enable agent forwarding.
  # Default value: false
  # config.ssh.forward_agent = true

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder ".", "/vagrant", type: "virtualbox"
  #config.vm.synced_folder "./data", "/opt/dataset" , type: "virtualbox"
  #config.vm.synced_folder "./code", "/home/vagrant/code" , type: "virtualbox"
  #config.vm.synced_folder "./mavendeps", "/root/.m2" , type: "virtualbox"

  
  
  
  
  # fix for windows executable bit on ansible provisioning
  config.vm.synced_folder ".", "/vagrant", :mount_options => ["dmode=777","fmode=666"]




  # start ansible provision
  config.vm.provision :ansible_local do |ansible|
    ansible.playbook = 'ansible/provision.yml'
    ansible.inventory_path = 'hosts'
    ansible.limit = 'all'
    ansible.verbose = true
    ansible.install = true
    ansible.become = true
	ansible.version = "latest" 
  end

  

  # A message to show after vagrant up
  config.vm.post_up_message = "Datahack Spark module box by Angel Conde"
end
