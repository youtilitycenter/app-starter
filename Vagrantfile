Vagrant.configure(2) do |config|
    config.vm.box = "ubuntu/xenial64"

    config.vm.network "private_network", ip: "192.168.100.100"

    config.vm.provider :virtualbox do |vb|
        vb.customize ["modifyvm", :id, "--memory", "2048"]
        vb.customize ["modifyvm", :id, "--cpus", "1"]

        vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
        vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
    end

#     config.vm.synced_folder ".", "/var/www/", id: "www-data", mount_options: ["rw", "tcp", "nolock", "noacl", "async"], type: "nfs", nfs_udp: false

    config.vm.synced_folder ".", "/var/www/", type: "virtualbox",
      :owner => 'www-data',
      :group => 'www-data',
      :mount_options => ['dmode=775', 'fmode=775']

    config.vm.synced_folder ".", "/vagrant", disabled: true
    config.vm.provision "shell", path: "dist/script/vagrant.sh"
#     config.vm.provision "shell", path: "dist/script/dependencies.sh"

    config.vm.hostname = "youtility-starter"
    config.hostsupdater.aliases = [
        "my.site.com"
    ]
end
