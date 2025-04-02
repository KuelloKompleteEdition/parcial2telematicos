Vagrant.configure("2") do |config|

    config.vm.define "firewall" do |firewall|
      firewall.vm.box = "bento/ubuntu-22.04"
      firewall.vm.network "private_network", ip: "192.168.56.9"
      firewall.vm.hostname = "firewall.empresa.local"
      firewall.vm.provision "shell", inline: <<-SHELL
        sudo apt update && sudo apt install -y ufw
      SHELL
    end

    config.vm.define "maestro" do |maestro|
      maestro.vm.box = "bento/ubuntu-22.04"
      maestro.vm.network "private_network", ip: "192.168.56.10"
      maestro.vm.network "forwarded_port", guest: 80, host: 3333
      maestro.vm.hostname = "maestro.empresa.local"
      maestro.vm.provision "shell", inline: <<-SHELL
        sudo apt update && sudo apt install -y bind9 bind9utils bind9-doc
      SHELL
    end
  
    config.vm.define "esclavo" do |esclavo|
      esclavo.vm.box = "bento/ubuntu-22.04"
      esclavo.vm.network "private_network", ip: "192.168.56.11"
      esclavo.vm.hostname = "esclavo.empresa.local"
      esclavo.vm.provision "shell", inline: <<-SHELL
        sudo apt update && sudo apt install -y bind9 bind9utils bind9-doc
      SHELL
    end

end