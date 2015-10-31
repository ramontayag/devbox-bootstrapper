# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

require "yaml"
CONFIG = YAML.load_file(File.expand_path("../box.yml", __FILE__))

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.hostname = 'dev-box'

  config.vm.provider :digital_ocean do |provider, override|
    override.ssh.private_key_path = CONFIG['private_key_path']
    override.vm.box = 'digital_ocean'
    override.vm.box_url = "https://github.com/smdahlen/vagrant-digitalocean/raw/master/box/digital_ocean.box"

    # provider.client_id = CONFIG['client_id']
    # provider.api_key = CONFIG['api_key']
    provider.ssh_key_name = CONFIG['key_name']
    provider.token = CONFIG['token']
    provider.image = 'ubuntu-14-04-x64'
    provider.region = CONFIG['region']
    provider.size = CONFIG['size']

    config.vm.synced_folder "mnt", "/vagrant", type: "rsync", rsync_exclude: ".git/"
  end
end
