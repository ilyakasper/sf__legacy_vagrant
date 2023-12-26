# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"

   config.vm.provision "shell", inline: <<-SHELL
	sudo apt-get install make -y
	sudo apt-get install gcc -y
	sudo apt-get install libreadline6 libreadline6-dev -y
	sudo apt-get install zlib1g-dev -y
	sudo apt-get install bison -y
	wget --quiet --no-check-certificate https://ftp.postgresql.org/pub/source/v8.4.22/postgresql-8.4.22.tar.gz
	tar xfz postgresql-8.4.22.tar.gz
	cd postgresql-8.4.22
	./configure
	make
	su
	make install
	adduser postgres
	mkdir /usr/local/pgsql/data
	chown postgres /usr/local/pgsql/data
	su - postgres
	/usr/local/pgsql/bin/initdb -D /usr/local/pgsql/data
	/usr/local/pgsql/bin/postgres -D /usr/local/pgsql/data >logfile 2>&1 &
	/usr/local/pgsql/bin/createdb code
	/usr/local/pgsql/bin/psql code
	sudo apt-get update    
   SHELL
end
