# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.hostname = "gitwarden-agent-tester"
  config.vm.provider "virtualbox" do |v|
    v.memory = 512
    v.cpus = 1
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "tests/test.yml"
    ansible.sudo = true
    ansible.host_key_checking = false
    ansible.extra_vars = {
      gitwarden_api_key_id: ENV['GITWARDEN_API_KEY'],
      gitwarden_api_key_secret: ENV['GITWARDEN_API_SECRET']
    }
  end
end
