Vagrant.configure("2") do |config|
    config.vm.box = "geerlingguy/ubuntu2004"
  
    # Forward ports for the frontend, backend, and Database
    config.vm.network "forwarded_port", guest: 3000, host: 3000  # Frontend
    config.vm.network "forwarded_port", guest: 5000, host: 5000  # Backend
    config.vm.network "forwarded_port", guest: 27017, host: 27017  # MongoDB
  
    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
    end
  
  end