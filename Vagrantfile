# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "CentOS-6.4-x86_64-minimal"

  config.vm.synced_folder ".", "/etc/puppet/modules/maven"
  config.vm.synced_folder "spec/fixtures/modules/wget", "/etc/puppet/modules/wget"
  config.vm.synced_folder "lib/facter", "/var/lib/puppet/lib/facter"

  # install the java module
  config.vm.provision :shell, :inline => "test -d /etc/puppet/modules/java || puppet module install puppetlabs/java -v 0.3.0"

  config.vm.provision :puppet do |puppet|
    puppet.manifests_path = "tests"
    puppet.manifest_file  = "init.pp"
  end

end
