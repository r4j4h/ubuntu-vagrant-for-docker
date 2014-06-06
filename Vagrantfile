    VAGRANTFILE_API_VERSION = "2"

    Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|


      # Install box

      config.vm.box = "phusion-open-ubuntu-12.04-amd64"
      config.vm.box_url = "https://oss-binaries.phusionpassenger.com/vagrant/boxes/ubuntu-12.04.3-amd64-vbox.box"

      config.vm.provider :vmware_fusion do |f, override|
        override.vm.box_url = "https://oss-binaries.phusionpassenger.com/vagrant/boxes/ubuntu-12.04.3-amd64-vmwarefusion.box"
      end


      # Install Docker

      if Dir.glob("#{File.dirname(__FILE__)}/.vagrant/machines/default/*/id").empty?
        # Install Docker
        pkg_cmd = "wget -q -O - https://get.docker.io/gpg | apt-key add -;" \
          "echo deb http://get.docker.io/ubuntu docker main > /etc/apt/sources.list.d/docker.list;" \
          "apt-get update -qq; apt-get install -q -y --force-yes lxc-docker; "
        # Add vagrant user to the docker group
        pkg_cmd << "usermod -a -G docker vagrant; "
        config.vm.provision :shell, :inline => pkg_cmd
      end


      # Forward Ports

      config.vm.network :private_network, ip: "192.168.50.4"


    end

