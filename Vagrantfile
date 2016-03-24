# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.network 'forwarded_port', guest: 3000, host: 3000
  config.vm.network 'forwarded_port', guest: 80, host: 8080

  # Development VM
  config.vm.define "dev", primary: true do |dev|
    dev.vm.box = "ubuntu/trusty64"
    dev.vm.provision "ansible" do |ansible|
      ansible.playbook = 'provisioning/dev.yml'
      ansible.verbose = 'vvv'
    end
  end

  # Production VM
  # config.vm.define "prod", autostart: false do |prod|
  #   prod.vm.box = "ubuntu/trusty64"
  #   prod.vm.provision "ansible" do |ansible|
  #     ansible.playbook = 'provisioning/prod.yml'
  #     ansible.verbose = 'vvv'
  #   end
  # end

  if Vagrant.has_plugin?('vagrant-cachier')
    config.cache.scope = :box
  else
    puts "Run `vagrant plugin install vagrant-cachier`"
  end

end
