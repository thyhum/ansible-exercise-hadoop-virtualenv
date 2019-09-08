# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'yaml'
dir        = File.dirname(File.expand_path(__FILE__))
config_yml = YAML.load_file("#{dir}/Vagrantfile.config.yml")

Vagrant.configure("2") do |config|

  config.ssh.insert_key      = false
  config.vm.box_check_update = false
  
  # # Install vagrant-vbguest if you want to auto update vbguest-tool
  # config.vbguest.auto_update = true
  config.vm.synced_folder '.', '/vagrant',  type: 'virtualbox', mount_options: ["dmode=755,fmode=755"], automount: true

  config_yml["vms"].each do |machine|

    config.vm.define machine["name"],
      primary:       machine['primary']   || false,
      autostart:     machine['autostart'] || false do |vm_config|
    
        vm_config.vm.hostname = machine['name']
        vm_config.vm.box      = machine["box"]
        
        vm_config.vm.network "forwarded_port", guest: 22, host: machine["ssh_port"]

    end

  end

end
