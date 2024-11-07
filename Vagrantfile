Vagrant.configure("2") do |config|
    # Definición de la máquina virtual
    config.vm.box = "ubuntu/bionic64"  # Puedes cambiar la caja si prefieres otra distribución
    config.vm.network "private_network", ip: "192.168.50.10"  # IP estática para acceder a la máquina
    
    # Configuración de la memoria y CPU
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  
    # Instalación y configuración de Apache
    config.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y apache2
      rm -rf /var/www/html  # Eliminamos el directorio por defecto de Apache
      ln -s /vagrant/web /var/www/html  # Vinculamos el directorio local al de Apache
    SHELL
  
    # Sincronización del directorio local 'web' con el directorio de Apache
    config.vm.synced_folder "./web", "/vagrant/web"
  end
  