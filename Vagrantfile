# -*- mode: ruby -*-
# vi: set ft=ruby :

# Define
VAGRANTFILE_API_VERSION = "2"
VM_BOX = "bento/centos-7.4"
VM_PARAMS = [
  { :hostname => "tmp01",:private_ip => "192.168.33.201",:shared_source => "../../",:shared_target => "/share"},
  { :hostname => "tmp02",:private_ip => "192.168.33.202",:shared_source => "../../",:shared_target => "/share"},
]

# Configure
Vagrant.configure(VAGRANTFILE_API_VERSION) { |config|

  config.vm.box = VM_BOX

  VM_PARAMS.each { |vm_param|
    config.vm.define vm_param[:hostname] { |node|
      node.vm.hostname = vm_param[:hostname]
      node.vm.network :private_network, ip: vm_param[:private_ip]
      node.vm.synced_folder vm_param[:shared_source], vm_param[:shared_target], mount_options: ['dmode=777','fmode=777'],owner: 0,group: 0
    }
  }
}
