# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  config.vm.box = "generic/centos8"
  config.vm.box_check_update = true

  config.vm.define "jmeter" do |server|
      server.vm.hostname = "jmeter"
      server.vm.provider "virtualbox" do |v|
          v.name = "jmeter"
          v.memory = 2048
          v.cpus = 2
          v.linked_clone = true
          v.gui = false
      end
      config.vm.synced_folder "./provisioning", "/home/vagrant/provisioning", create: false, type: "rsync", rsync__auto: true, rsync__args: ["--verbose", "--archive", "-z", "--copy-links"]
      config.vm.synced_folder "./projects", "/home/vagrant/projects"
      server.vm.provision "ansible_local" do |ansible|
          ansible.provisioning_path = "/home/vagrant/provisioning/"
          ansible.extra_vars = { ansible_python_interpreter:"/usr/bin/python3" }
          ansible.playbook = "jmeter.yml"
          #ansible.compatibility_mode = "2.0"
      end
  end
end