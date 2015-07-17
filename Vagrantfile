VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
	# Configure The Box
	config.vm.box = "ubuntu/trusty64"
	config.vm.hostname = "drinkaccounting"

	config.vm.network :private_network, ip: "192.168.33.10"

	config.vm.provider "virtualbox" do |vb|
	  vb.customize ["modifyvm", :id, "--memory", "2048"]
	  vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
	  vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
	  vb.cpus = 2
	end

	# Configure Port Forwarding
	# Website
	config.vm.network "forwarded_port", guest: 80, host: 8000
	# MySQL
	config.vm.network "forwarded_port", guest: 3306, host: 33060
	# Livereload
	config.vm.network "forwarded_port", guest: 35729, host: 35729
	# Mailcatcher
	config.vm.network "forwarded_port", guest: 1080, host: 10800
	# PhpMyAdmin
	config.vm.network "forwarded_port", guest: 1085, host: 10850

	# Run The Base Provisioning Script
	config.vm.provision "shell" do |s|
	  s.path = "./scripts/provision.sh"
	end

	# Sync folder between vm and host
	config.vm.synced_folder "html/", "/var/www/html"
end
