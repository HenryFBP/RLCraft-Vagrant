# frozen_string_literal: true

MEMORY = 5120
CORES = 4

Vagrant.configure('2') do |config|
  config.vm.box = 'hashicorp/bionic64'

  config.vm.network "forwarded_port", guest: 25565, host: 25565

  config.ssh.username = 'vagrant'
  config.ssh.password = 'vagrant'
  config.ssh.insert_key = false

  # Disable default synced folder
  config.vm.synced_folder '.', '/vagrant', disabled: true

  config.vm.synced_folder './persistent', '/minecraft/persistent/'

  config.vm.provision 'shell', path: 'install-tools.sh', run: 'once'

  config.vm.provision 'shell', path: 'download-deps.sh', run: 'always'

  config.vm.provider 'virtualbox' do |v|
    v.memory = MEMORY
    v.cpus = CORES
  end
end
