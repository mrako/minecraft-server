Vagrant.configure("2") do |config|
  config.vm.box      = "ubuntu/xenial64"

  config.vm.network :forwarded_port, guest: 25565, host: 25565, auto_correct: false

  config.ssh.forward_agent = true
  config.ssh.insert_key = true
  
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", 4096]
    vb.customize ["modifyvm", :id, "--cpus", 2]
  end

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "provisioning/playbook.yml"

    ansible.host_key_checking = false
  end
end
