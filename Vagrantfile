Vagrant.configure("2") do |config|

 config.vm.box = "ubuntu/mantic64"
 config.vm.hostname = "vm1"
 config.vm.network "private_network", ip: "192.168.56.1"
 #make local file or folder available in vagrant box
 config.vm.synced_folder "./data", "/home/vagrant/data"
 #copy from local host to vagrant box
 config.vm.provision "file", source: "copiedfile.txt", destination: "/home/vagrant/copiedfile.txt"

 config.vm.provider :virtualbox do |vb|
  vb.customize ["modifyvm", :id, "--memory", 1024]
  vb.customize ["modifyvm", :id, "--cpus", 2]
 end
end

