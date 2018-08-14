# -*- mode: ruby -*-
# vi: set ft=ruby :

domain = 'test'
name   = 'oriole-dev'
ip     = '10.11.19.101'

Vagrant.configure("2") do |config|

  config.vm.box = "folio/stable-backend"

  config.vm.provider "virtualbox" do |vb|
    vb.name = "#{name}.#{domain}"
    vb.linked_clone = true
  end

  config.vm.hostname = "#{name}.#{domain}"
  config.vm.network 'private_network', ip: ip
  #config.hostsupdater.aliases = [ 'dev.oriole.library.jhu.edu']

  config.vm.provision 'ansible' do |ansible|
    ansible.compatibility_mode = '2.0'
    ansible.inventory_path = 'inventory' 
    # ensure roles installed
    #ansible.galaxy_role_file = 'requirements.yml'
    ansible.verbose = 'v'
    ansible.playbook = 'setup.yml'
  end
end
