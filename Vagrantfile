VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(2) do |config|
  config.vm.define "pypi" do |pypi|
    pypi.vm.box = "ubuntu/trusty64"
    pypi.vm.hostname = 'pypi'
    pypi.vm.network :private_network, ip: "192.168.56.101"

    pypi.vm.provider "virtualbox" do |v|
      v.memory = 4096
    end

    pypi.vm.network "forwarded_port", guest: 8080, host: 8080

    # we will use docker and docker-compose for running our services so lets get it installed here
    pypi.vm.provision :docker
    pypi.vm.provision :docker_compose
  end

  config.vm.define "app" do |app|
    app.vm.box = "ubuntu/trusty64"
    app.vm.hostname = 'app'
    app.vm.network :private_network, ip: "192.168.56.102"

    app.vm.provider "virtualbox" do |v|
      v.memory = 4096
    end

    # we will use docker and docker-compose for running our services so lets get it installed here
    app.vm.provision :docker
    app.vm.provision :docker_compose
  end


end
