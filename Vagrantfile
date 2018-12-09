# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "tiflash/bionic64"
  config.vm.box_url = "https://cjwebb.io/downloads/vagrant/ubuntu/bionic64.box"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "./", "/develop"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
    # Customize the amount of memory on the VM:
    vb.memory = "1024"
  end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
  config.vm.provision "ansible" do |ansible|
    ansible.galaxy_role_file = "./provisioning/requirements.yml"
    ansible.extra_vars = {
      ansible_python_interpreter: "/usr/bin/python3",
      ccs_prefix: "/home/{{ ansible_user }}/ti",
      ccs_major_version: "8",
      ccs_minor_version: "2",
      ccs_patch_version: "0",
      ccs_build_version: "00007",

      python_versions: [
        { version: "3.6.6" }
      ]
    }
    ansible.playbook = "./provisioning/playbook.yml"
  end
end
