# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "generic/alpine312"
  config.vm.network "forwarded_port", guest: 80, host: 8081
  config.vm.provision "file", source: "conf", destination: "$HOME/conf"
  config.vm.provision "shell", inline: <<-SHELL
    apk update
    apk add nginx iproute2
    rc-update add nginx
    cp /home/vagrant/conf/default.conf /etc/nginx/conf.d/default.conf
    rc-service nginx restart
  SHELL
end
