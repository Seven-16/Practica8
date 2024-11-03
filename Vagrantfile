Vagrant.configure("2") do |config|
    # Usa una box base de Ubuntu (o la que prefieras)
    config.vm.box = "ubuntu/jammy64"
  
    # Configuración de la memoria RAM y número de CPUs
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 2
    end
    
    # Mapea el puerto 8080 del host al puerto 80 de la VM
    config.vm.network "forwarded_port", guest: 80, host: 8080
  
    # Instala Apache y configura el directorio compartido
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      sudo rm -rf /var/www/html
      sudo ln -fs /vagrant /var/www/html
    SHELL
  
    # Comparte el directorio local con Apache
    config.vm.synced_folder ".", "/vagrant", type: "virtualbox"
  end
  