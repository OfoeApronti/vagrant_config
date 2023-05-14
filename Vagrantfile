Vagrant.configure("2") do |config|

 servers=[
  {
    :hostname => "Server1",
    :box => "ubuntu/mantic64",
    :ip => "192.168.56.5",
    :ssh_port => '2205'
  },
  {
    :hostname => "Server2",
    :box => "ubuntu/mantic64",
    :ip => "192.168.56.10",
    :ssh_port => '2210'
  },
  {
    :hostname => "Server3",
    :box => "ubuntu/mantic64",
    :ip => "192.168.56.15",
    :ssh_port => '2215'
  },
 ]

 servers.each do |machine|
  config.vm.define machine[:hostname] do |node|
    node.vm.box=machine[:box]
    node.vm.hostname=machine[:hostname]
    node.vm.network :private_network, ip:machine[:ip]
    node.vm.network "forwarded_port", guest: 22, host: machine[:ssh_port], id: "ssh"
    #make local file or folder available in vagrant box
    node.vm.synced_folder "./data", "/home/vagrant/data"
    #copy from local host to vagrant box
    node.vm.provision "file", source: "copiedfile.txt", destination: "/home/vagrant/copiedfile.txt"

    node.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", 1024]
      vb.customize ["modifyvm", :id, "--cpus", 2]
     end
  end
 end
end

