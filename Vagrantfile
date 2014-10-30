Vagrant.configure("2") do |config|
	config.vm.box = "heroku"
	config.vm.box_url = "http://dl.dropbox.com/u/1906634/heroku.box"
	config.vm.network "private_network", ip: "192.168.50.15"
	src_dir = './'
	doc_root = '/vagrant_data/'
	app_root = '/vagrant_data/'
	config.vm.synced_folder src_dir, "/vagrant_data", :create => true, :owner=> 'vagrant', :group=>'www-data', :mount_options => ['dmode=775,fmode=775']
	config.vm.provision :chef_solo do |chef|
		chef.cookbooks_path = "cookbooks"
		chef.add_recipe "apt"
		chef.add_recipe "php55_nginx"
		# chef.add_recipe "local_db"
		# chef.add_recipe "local_etc"
		# chef.add_recipe "deploy_cake_local"
		chef.json = {doc_root: doc_root,app_root: app_root}
	end
end