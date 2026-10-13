
Vagrant.configure("2") do |config|
  
config.vm.box = "debian/bookworm64"

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
config.vm.define "dhcp" do |srv|
    srv.vm.network "public_network", bridge: "enp0s3"
    srv.vm.network "private_network", ip: "192.168.57.10", virtualbox__intnet: "intnet"
  end

  config.vm.define "c1" do |c1|
    c1.vm.network "private_network", type: "dhcp", virtualbox__intnet: "intnet"
  end

  config.vm.define "printer" do |p|
    p.vm.network "private_network", mac: "080027EF4B7E", type: "dhcp", virtualbox__intnet: "intnet"
  end
end

