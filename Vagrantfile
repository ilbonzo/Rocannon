Vagrant.configure("2") do |config|
  config.vm.box = "debian/jessie64"

  config.vm.hostname = "rocannon"

  config.vm.network :forwarded_port, guest: 80, host: 4444
  config.vm.network "private_network", ip: "192.168.33.66"

  config.ssh.forward_agent = true

  # config.vm.provision "shell",
    # inline: "sudo apt-get -y update && sudo apt-get -y install lynx"


  config.vm.provision :ansible do |ansible|
    ansible.groups = {
      "development" => ["default"],
      "all_groups:children" => ["development"]

    }
    ansible.playbook = "ansible/playbook.yml"
  end

end
