VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "centos"
  config.ssh.forward_agent = true
  config.vm.synced_folder "my_site_folder", "/var/www"

  config.vm.define "web" do |web|
    web.vm.network "private_network", ip: "10.0.20.10"

    web.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
    end
  end

  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

end
