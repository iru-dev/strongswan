nodes = [
  { :hostname => 'strongswan', :ip => '172.30.0.100'}
]

Vagrant.configure("2") do |config|
  nodes.each do |node|
    config.vm.define node[:hostname] do |nodeconfig|
      nodeconfig.vm.box = "centos/8"
      nodeconfig.vm.hostname = node[:hostname]

      nodeconfig.vm.network :private_network, ip: node[:ip]
      memory = node[:ram] ? node[:ram] : 1024;
      nodeconfig.vm.provider :virtualbox do |vb|
        vb.customize [
          "modifyvm", :id,
          "--memory", memory.to_s,
        ]
      end
      ssh_pub_key = File.readlines("/home/iru/.ssh/id_ecdsa.pub").first.strip

        nodeconfig.vm.provision 'shell', inline: "echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys", privileged: false
        nodeconfig.vm.provision 'shell', inline: "hostname #{node[:hostname]};echo #{node[:hostname]} > /etc/hostname"
    end
    config.hostmanager.enabled = true
    config.hostmanager.manage_guest = true
  end
end
