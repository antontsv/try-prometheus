# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial-cloud"
  config.vm.box_url = "https://cloud-images.ubuntu.com/xenial/20170311/xenial-server-cloudimg-amd64-vagrant.box"
  config.vm.network "private_network", ip: "10.100.100.121"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = 1024
  end

  config.vm.provision "shell", inline: <<-SHELL
     prom_ver="1.7.1"
     prom_ver_full="prometheus-$prom_ver.linux-amd64"
     wget -q "https://github.com/prometheus/prometheus/releases/download/v$prom_ver/$prom_ver_full.tar.gz"
     [ $? -eq 0 ] || (echo "Cannot download prometheus" && exit 1)
     echo "Extracting from archive..." && tar -xf "$prom_ver_full.tar.gz"
     rm "$prom_ver_full.tar.gz"
     [ -d "$prom_ver_full" ] || ( echo "Failed to get prometheus dir from archive." && exit 1)
     cd "$prom_ver_full" && nohup ./prometheus > prometheus.log 2>&1 &
     echo "Open 😯  http://10.100.100.121:9090 in your browser"
  SHELL
end
