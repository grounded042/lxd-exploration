$setup_script = <<-SCRIPT
apt update
apt upgrade -y
cat <<EOF | sudo lxd init --preseed
config:
  core.https_address: '[::]:8443'
  core.trust_password: password
networks:
- config:
    ipv4.address: auto
    ipv6.address: none
  description: ""
  managed: false
  name: lxdbr0
  type: ""
storage_pools:
- config: {}
  description: ""
  name: default
  driver: dir
profiles:
- config: {}
  description: ""
  devices:
    eth0:
      name: eth0
      nictype: bridged
      parent: lxdbr0
      type: nic
    root:
      path: /
      pool: default
      type: disk
  name: default
cluster: null
EOF
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/cosmic64"

  config.vm.provision "shell", inline: $setup_script

  config.vm.network "forwarded_port", guest: 8443, host: 8443
end

