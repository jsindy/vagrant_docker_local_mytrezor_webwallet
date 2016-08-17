# -*- mode: ruby -*-
# vi: set ft=ruby :
#by Joshua Sindy 2014

$script = <<SCRIPT

#Building Vagrant Docker VM
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 36A1D7869245C8950F966E92D8576A8BA88D21E9
sudo sh -c "echo deb https://get.docker.com/ubuntu docker main > /etc/apt/sources.list.d/docker.list"
sudo apt-get update
sudo apt-get -y install linux-image-extra-$(uname -r) aufs-tools vim bridge-utils curl
sudo apt-get -y install lxc-docker
#sudo echo -e 'DOCKER_OPTS="--bip=10.66.33.10/24 --dns 8.8.4.4 --dns 8.8.8.8"' | sudo tee -a /etc/default/docker

#add docker dynamic memory support
sudo sed -i 's/GRUB_CMDLINE_LINUX=""/GRUB_CMDLINE_LINUX="cgroup_enable=memory swapaccount=1"/g' /etc/default/grub
sudo update-grub
sudo git clone https://github.com/jsindy/mytrezor_docker.git
sudo docker build --no-cache -t mytrezor_prod /home/vagrant/mytrezor_docker/prod/
sudo docker run -p 8000:8000 -d mytrezor_prod grunt server

SCRIPT

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.hostname = "docker01"

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"
  config.vm.network "forwarded_port", guest: 8000, host: 8000
  config.vm.provider "virtualbox" do |v|
  v.memory = 2048
  v.cpus = 2
  end
  config.vm.provision "shell", inline: $script
end
