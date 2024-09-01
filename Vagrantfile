Vagrant.configure('2') do |config|
  config.vm.box = 'ubuntu/bionic64'
  config.env.enable

  config.vm.hostname = 'moodle'
  config.vm.network :private_network, ip: ENV['VM_IP']

  config.vm.network 'forwarded_port', guest: 80, host: ENV['HTTP_PORT']
  config.vm.network 'forwarded_port', guest: 443, host: ENV['HTTPS_PORT']

  config.vm.provider :virtualbox do |vb|
    vb.gui = false
    vb.cpus = ENV['VM_CPUS']
    vb.memory = ENV['VM_MEMORY']
    vb.customize ['modifyvm', :id, '--natdnsproxy1', 'off']
    vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'off']
  end
  config.disksize.size = ENV['VM_DISKSIZE']

  config.vm.provision :shell, inline: "apt-get update"
  config.vm.provision :docker
  config.vm.provision :docker_compose,
    env: {
      :DB_USERNAME => ENV['DB_USERNAME'],
      :DB_PASSWORD => ENV['DB_PASSWORD'],
      :DB_DATABASE => ENV['DB_DATABASE'],
      :DB_ROOT_PASSWORD => ENV['DB_ROOT_PASSWORD'],
    },
    yml: '/vagrant/docker-compose.yml',
    run: 'always'
end
