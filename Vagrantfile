Vagrant.configure("2") do |config|

  config.vm.define "venus" do |venus|
   venus.vm.box = "debian/bullseye64"
   venus.vm.hostname = "venus.sistema.test"
   venus.vm.network "private_network", ip: "192.168.57.102"

   venus.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y bind9
    SHELL
    
   venus.vm.provision "shell", inline: <<-SHELL
    cp /vagrant/confg/slave/named.conf.local /etc/bind/named.conf.local
    systemctl restart bind9
   SHELL

  
 end

 config.vm.define "tierra" do |tierra|
   tierra.vm.box = "debian/bullseye64"
   tierra.vm.hostname = "tierra.sistema.test"
   tierra.vm.network "private_network", ip: "192.168.57.103"

   tierra.vm.provision "shell", inline: <<-SHELL
        apt-get update
        apt-get install -y bind9
      SHELL

   tierra.vm.provision "shell", inline: <<-SHELL
      cp /vagrant/confg/master/named.conf.local /etc/bind/named.conf.local
      cp /vagrant/confg/master/db.sistema.test /etc/bind/db.sistema.test
      cp /vagrant/confg/master/db.192.168.57 /etc/bind/db.192.168.57
      systemctl restart bind9
    SHELL

 end
end

