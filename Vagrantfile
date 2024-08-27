# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Especifica a box a ser utilizada
  config.vm.box = "ubuntu/focal64"

  # Configura a rede, redirecionando a porta 8080 do host para a porta 80 do guest
  config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Script de provisionamento
  config.vm.provision "shell", inline: <<-SHELL
    echo "Installing Apache and setting it up..."
    apt-get update -y >/dev/null 2>&1
    apt-get install -y apache2 >/dev/null 2>&1

    cp -r /vagrant/html/* /var/www/html/

    systemctl start apache2
    systemctl enable apache2

    systemctl status apache2
  SHELL
end
