Run MyTrezor webwallet locally, powered by Vagrant and Docker
========================================

Prerequisites
=============

git http://git-scm.com/download/mac

vagrant https://www.vagrantup.com/downloads.html

virtualbox https://www.virtualbox.org/wiki/Downloads


Get started
=================

Add "127.0.0.1 localhost.mytrezor.com" to your HOSTS file

git clone https://github.com/jsindy/vagrant_docker_local_mytrezor_webwallet.git

cd vagrant_docker_local_mytrezor_webwallet/

vagrant up

WAIT, this will take a pretty long time as it builds everything from source.

Once completed navigate to http://localhost.mytrezor.com:8000
