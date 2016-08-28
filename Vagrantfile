Vagrant.configure('2') do |config|
  config.vm.box = 'ubuntu/xenial64'
  config.vm.box_url = 'https://atlas.hashicorp.com/ubuntu/boxes/xenial64'
  config.vm.box_check_update = true

  config.vm.network 'private_network', ip: '10.10.10.10'

  config.vm.provider 'virtualbox' do |vb|
    vb.gui = false
    vb.cpus = 2
    vb.memory = '2048'
    vb.customize ['modifyvm', :id, '--ioapic', 'on']
  end

  config.vm.synced_folder './work',
                          '/home/ubuntu/work',
                          type: 'rsync',
                          # 標準の設定から[--delete]のみ除外
                          rsync__args: ['--verbose', '--archive', '-z', '--copy-links'],
                          rsync__exclude: [
                            # Common
                            '.DS_Store',
                            '.git/',
                            '.gitkeep',
                            # sass
                            '.sass-cache/',
                            # Elixir
                            'deps/',
                            '_build/',
                            # Node.js
                            'node_modules/',
                            'typings/',
                            # for rails
                            '.bundle/',
                            'log/',
                            'tmp/',
                            'db/*.sqlite3',
                            'db/*.sqlite3-journal',
                            'coverage/',
                            'spec/tmp/',
                            'vendor/bundle/',
                            # for php(remove if you create ruby apps)
                            'vendor/'
                          ]
  config.vm.synced_folder './ansible', '/var/ansible', nfs: true
  config.vm.provision 'ansible_local' do |ansible|
    ansible.provisioning_path = '/var/ansible'
    ansible.inventory_path = '/var/ansible/hosts'
    ansible.playbook = './vagrant.yml'
    ansible.limit = 'all'
    ansible.verbose = 'vv'
  end
end
