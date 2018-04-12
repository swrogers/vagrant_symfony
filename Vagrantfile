Vagrant.configure(2) do |config|
    
    config.vm.define "symfony" do |symfony|
        # Base template for virtualbox
        symfony.vm.box = "ubuntu/trusty64"
        
        symfony.vm.hostname = "symfony.dev"
        
        symfony.vm.network :private_network, ip: "192.168.33.151"
        # symfony.vm.network "forwarded_port", guest:80, host:8000
        
        # Using ansible_local since I'm on Windows
        symfony.vm.provision :ansible_local do |ansible|
            ansible.playbook = "provisioning/playbook.yml"
        end
    end
    
    config.vm.synced_folder ".", "/vagrant"
    
    config.vm.provider "virtualbox" do |v|
        v.memory = 1024
        v.cpus = 2
    end
end