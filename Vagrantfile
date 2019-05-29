Vagrant.configure("2") do |config|
 # config.ssh.insert_key = false
#  config.vm.provider :vmare_desktop do |vmware|
#       vmware.vmx["ethernet0.pcislotnumber"] = "32"
#  end
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.manage_guest = true
  config.hostmanager.ignore_private_ip = false
  config.hostmanager.include_offline = true
  #config.landrush.enabled = true
  #config.landrush.tld = 'ravi.local'
  #config.landrush.guest_redirect_dns = false


  config.vm.define "master" do |master|
    master.vm.box = "centos/7"
    master.vm.hostname = "master.ravi.local"
    master.vm.network :forwarded_port, guest: 22, host: 2222, id: "ssh", disabled: true
    master.vm.network :forwarded_port, guest: 22, host: 2230, auto_correct: true
    master.vm.network "private_network", ip: "172.16.121.120"
    master.vm.synced_folder ".", "/vagrant", type: 'sshfs', create:true 
    master.vm.provision "ansible" do |ansible|
      ansible.playbook = "master_kube.yml"
    end

  end

  config.vm.define "node1" do |node1|
    node1.vm.box = "centos/7"
    node1.vm.hostname = "node1.ravi.local"
    node1.vm.network :forwarded_port, guest: 22, host: 2222, id: "ssh", disabled: true
    node1.vm.network :forwarded_port, guest: 22, host: 2231, auto_correct: true
    node1.vm.network "private_network", ip: "172.16.121.121"
    node1.vm.synced_folder ".", "/vagrant", type: 'sshfs', create:true 
    node1.vm.provision "ansible" do |ansible|
      ansible.playbook = "node_kube.yml"
    end
  end

  config.vm.define "node2" do |node2|
    node2.vm.box = "centos/7"
    node2.vm.hostname = "node2.ravi.local"
    node2.vm.network :forwarded_port, guest: 22, host: 2222, id: "ssh", disabled: true
    node2.vm.network :forwarded_port, guest: 22, host: 2232, auto_correct: true
    node2.vm.network "private_network", ip: "172.16.121.122"
    node2.vm.synced_folder ".", "/vagrant", type: 'sshfs', create:true 
    node2.vm.provision "ansible" do |ansible|
      ansible.playbook = "node_kube.yml"
    end
  end

  config.vm.define "node3" do |node3|
    node3.vm.box = "centos/7"
    node3.vm.hostname = "node3.ravi.local"
    node3.vm.network :forwarded_port, guest: 22, host: 2222, id: "ssh", disabled: true
    node3.vm.network :forwarded_port, guest: 22, host: 2233, auto_correct: true
    node3.vm.network "private_network", ip: "172.16.121.123"
    node3.vm.synced_folder ".", "/vagrant", type: 'sshfs', create:true 
    node3.vm.provision "ansible" do |ansible|
      ansible.playbook = "node_kube.yml"
    end
  end

  config.vm.provider "virtualbox" do |v|
    v.memory = 4000
    v.cpus = 2
  end
end
