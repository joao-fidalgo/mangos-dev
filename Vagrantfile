# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "fgrehm/trusty64-lxc"

  config.vm.network "forwarded_port", guest: 3306, host: 3306 # mysqld
  config.vm.network "forwarded_port", guest: 3724, host: 3724 # realmd
  config.vm.network "forwarded_port", guest: 8085, host: 8085 # mangosd

  config.vm.define "classic", autostart: false do |classic|

  end

  config.vm.define "tbc", autostart: false do |tbc|

  end

  config.vm.define "wotlk", autostart: false do |wotlk|

  end

  config.vm.provision "ansible" do |ansible|
    ansible.groups = {
      "dev"     => [ "classic", "tbc", "wotlk" ],
      "classic" => [ "classic" ],
      "tbc"     => [ "tbc" ],
      "wotlk"   => [ "wotlk" ]
    }

    ansible.playbook = "ansible/mangos.yml"
  end

end
