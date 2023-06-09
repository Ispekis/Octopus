# -*- mode: ruby -*-
# vi: set ft=ruby :

SSH_key = ENV['OCTOPUS_SSH_PUBLIC_KEY']

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.

  config.vm.define "poll" do |poll|
    poll.vm.box = "debian/buster64"
    poll.vm.hostname = "poll"
    poll.vm.provider :virtualbox do |vb|
      vb.name = "poll VM"
    end
    poll.vm.provision "shell", inline: <<-SHELL
      echo "#{SSH_key}\n" >> /home/vagrant/.ssh/authorized_keys
    SHELL
    poll.vm.network "private_network", ip: "192.168.56.10"
    # poll.vm.network "forwarded_port", guest: 22, host: 2222, host_ip: "192.168.0.106", id: "ssh"
  end

  config.vm.define "result" do |result|
    result.vm.box = "debian/buster64"
    result.vm.hostname = "result"
    result.vm.provider :virtualbox do |vb|
      vb.name = "result VM"
    end
    result.vm.provision "shell", inline: <<-SHELL
      echo "#{SSH_key}\n" >> /home/vagrant/.ssh/authorized_keys
    SHELL
    result.vm.network "private_network", ip: "192.168.56.11"
    # result.vm.network "forwarded_port", guest: 22, host: 2200, host_ip: "192.168.0.107", id: "ssh"
  end

  config.vm.define "redis" do |redis|
    redis.vm.box = "debian/buster64"
    redis.vm.hostname = "redis"
    redis.vm.provider :virtualbox do |vb|
      vb.name = "redis VM"
    end
    redis.vm.provision "shell", inline: <<-SHELL
      echo "#{SSH_key}\n" >> /home/vagrant/.ssh/authorized_keys
    SHELL
    redis.vm.network "private_network", ip: "192.168.56.12"
    # redis.vm.network "forwarded_port", guest: 22, host: 2201, host_ip: "192.168.0.108", id: "ssh"
  end

  config.vm.define "worker" do |worker|
    worker.vm.box = "debian/buster64"
    worker.vm.hostname = "worker"
    worker.vm.provider :virtualbox do |vb|
      vb.name = "worker VM"
    end
    worker.vm.provision "shell", inline: <<-SHELL
      echo "#{SSH_key}\n" >> /home/vagrant/.ssh/authorized_keys
    SHELL
    worker.vm.network "private_network", ip: "192.168.56.13"
    # worker.vm.network "forwarded_port", guest: 22, host: 2202, host_ip: "192.168.0.109", id: "ssh"
  end

  config.vm.define "postgresql" do |postgresql|
    postgresql.vm.box = "debian/buster64"
    postgresql.vm.hostname = "postgresql"
    postgresql.vm.provider :virtualbox do |vb|
      vb.name = "postgresql VM"
    end
    postgresql.vm.provision "shell", inline: <<-SHELL
      echo "#{SSH_key}\n" >> /home/vagrant/.ssh/authorized_keys
    SHELL
    postgresql.vm.network "private_network", ip: "192.168.56.14"
    # postgresql.vm.network "forwarded_port", guest: 22, host: 2203, host_ip: "192.168.0.110", id: "ssh"
  end

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
end
