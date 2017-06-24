Vagrant.configure("2") do |config|

  config.vm.define "web1" do |web1|
    web1.vm.box = "debian/jessie64"
    web1.vm.hostname = "rocannon-web-1"
    web1.vm.network :forwarded_port, guest: 80, host: 4443
    web1.vm.network "private_network", ip: "192.168.33.65"
    web1.ssh.forward_agent = true
  end

  config.vm.define "web2" do |web2|
    web2.vm.box = "debian/jessie64"
    web2.vm.hostname = "rocannon-web-2"
    web2.vm.network :forwarded_port, guest: 80, host: 4444
    web2.vm.network "private_network", ip: "192.168.33.66"
    web2.ssh.forward_agent = true
  end

  config.vm.define "db" do |db|
    db.vm.box = "debian/jessie64"
    db.vm.hostname = "rocannon-db"
    db.vm.network "private_network", ip: "192.168.33.67"
    db.ssh.forward_agent = true
  end

  config.vm.define "lb" do |lb|
    lb.vm.box = "debian/jessie64"
    lb.vm.hostname = "rocannon-lb"
    lb.vm.network :forwarded_port, guest: 80, host: 4445
    lb.vm.network "private_network", ip: "192.168.33.68"
    lb.ssh.forward_agent = true
  end

  config.vm.provision :ansible do |ansible|
    ansible.groups = {
      "webserver" => ["web1" , "web2"],
      "dbserver" => ["db"],
      "loadbalancer" => ["lb"],
      "all_groups:children" => ["development"]

    }
    ansible.playbook = "ansible/playbook.yml"
  end

end
