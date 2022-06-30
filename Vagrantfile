# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.

    config.vm.define "consul-node" do |centos_node|
      centos_node.vm.box = "centos/stream8"
      centos_node.vm.network "private_network", type: "dhcp"
      centos_node.vm.hostname = "centos-node"
      config.vm.provider :virtualbox do |vb|
         vb.customize ["modifyvm", :id, "--memory", "3072"]
         vb.customize ["modifyvm", :id, "--cpus", "2"]
         vb.name = "consul-node"
      end
      centos_node.vm.provision "shell", inline: <<-SHELL
        sudo yum install -y yum-utils
        sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo
        sudo yum -y install consul
        sudo usermod -aG consul vagrant
        sudo yum install -y wget unzip glibc
        sudo wget https://github.com/tetratelabs/archive-envoy/releases/download/v1.22.2/envoy-v1.22.2-linux-amd64.tar.xz -O envoy.tar.xz
        tar xvf envoy.tar.xz
        rm envoy.tar.xz
        sudo cp envoy-v1.22.2-linux-amd64/bin/envoy /usr/local/bin
        wget https://github.com/hashicorp/demo-consul-101/releases/download/0.0.3.1/counting-service_linux_amd64.zip
        unzip counting-service_linux_amd64.zip
        wget https://github.com/hashicorp/demo-consul-101/releases/download/0.0.3.1/dashboard-service_linux_amd64.zip
        unzip dashboard-service_linux_amd64.zip
     SHELL
    end
end
