test_net="192.168.56."

NODE="ansible-node-"

DISTR="cyberdolphin_"

servers=[
  {
    :hostname => NODE + "master",
    :ip => test_net + "10",
    :distrib => DISTR + "ubuntu",
    :share_disable => false,
    :vbguest => true
  },
  {
    :hostname => NODE + "ubuntu",
    :ip => test_net + "110",
    :distrib => DISTR + "ubuntu",
    :share_disable => true,
    :vbguest => false
  },
  {
    :hostname => NODE + "debian",
    :ip => test_net + "120",
    :distrib => DISTR + "debian",
    :share_disable => true,
    :vbguest => false
  },
 {
    :hostname => NODE + "centos7",
    :ip => test_net + "130",
    :distrib => DISTR + "centos7",
    :share_disable => true,
    :vbguest => false
     },
  {
    :hostname => NODE + "centos8",
    :ip => test_net + "140",
    :distrib => DISTR + "centos8",
    :share_disable => true,
    :vbguest => false
     }
]


Vagrant.configure(2) do |config|
    
    config.ssh.username = "sadmin"
    
    config.ssh.private_key_path = "../ssh_auto/priv_cyber_openssh"
    
	servers.each do |machine|

		config.vm.define machine[:hostname] do |node|
            
            node.vm.synced_folder './data', '/vagrant', disabled: machine[:share_disable]
            
            node.vbguest.auto_update = machine[:vbguest]
			        
            node.vm.box = machine[:distrib]

			node.vm.hostname = machine[:hostname]
            
            node.vm.boot_timeout = 1000
  
            node.vm.network "private_network", ip: machine[:ip], name: "VirtualBox Host-Only Ethernet Adapter"

			node.vm.provider "virtualbox" do |vb|
				  
                                  vb.memory = "1024"
  
                                  vb.cpus = 1
			end
            
		end
	end
end
