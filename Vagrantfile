# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

   config.vm.define :hello do |hi|
     hi.vm.network :private_network, :ip => "192.168.33.10"
     hi.vm.provider "virtualbox" do |vb|
       vb.gui = false
        vb.customize ["modifyvm", :id, "--memory", "1024"]
     end
  
     hi.vm.provision "ansible" do |ansible|
        ansible.playbook = "webserver.yml"
        ansible.verbose = "vvv"
     end
   end

   config.vm.define :wordpress do |wp|
     wp.vm.network :private_network, :ip => "192.168.33.22"

     wp.vm.provision "ansible" do |ansible|
       ansible.playbook = "blog.yml"
       ansible.verbose = "vvv"
     end
   end 
end
