Vagrant.configure("2") do |config|
  # Use the official Ubuntu box from Vagrant Cloud
  config.vm.box = "ubuntu/bionic64"

  # Forward port 8000 on the host to port 8000 on the guest
  config.vm.network "forwarded_port", guest: 8000, host: 8000

  # Configure the virtual machine's provisioning
  config.vm.provision "shell", inline: <<-SHELL
    # Update and install required packages
    apt-get update
    apt-get install -y python3-pip python3-dev libpq-dev

    # Install virtualenv
    pip3 install virtualenv

    # Create a virtual environment
    cd /vagrant
    virtualenv venv

    # Activate the virtual environment and install Django
    source venv/bin/activate
    pip install django
  SHELL
end
