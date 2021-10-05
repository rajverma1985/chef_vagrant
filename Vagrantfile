# -*- mode: ruby -*-
# vi: set ft=ruby :

unless Vagrant.has_plugin?("vagrant-ohai")
  raise "vagrant-ohai plugin not installed! Install the plugin with command'vagrant plugin install vagrant-ohai'"
end

NODE_SCRIPT = <<EOF.freeze
  echo "Intial Node prep...."
  # ensure the time is up to date
  yum -y install ntp
  systemctl start ntpd
  systemctl enable ntpd
  curl -L https://omnitruck.chef.io/install.sh | sudo bash -s -- -v 16
EOF

def set_hostname(server)
  server.vm.provision 'shell', inline: "hostname #{server.vm.hostname}"
end

Vagrant.configure(2) do |config|

 config.vm.define 'chef_workstation' do |n|
    n.vm.box = 'bento/centos-7.2'
    n.vm.box_version = '2.3.1'
    n.vm.hostname = 'chef-ws'
    n.vm.network :private_network, ip: '192.168.1.50', nic_type: "virtio"
    n.vm.provision :shell, inline: NODE_SCRIPT.dup
   set_hostname(n)
  end
end
