require_relative './.vagrant/credentials'

Vagrant.configure("2") do |config|
config.vm.box = "dummy"

	config.vm.provider :aws do |aws, override|
    
		aws.access_key_id = ACCESS_KEY_ID
		aws.secret_access_key = SECRET_ACCESS_KEY
		aws.keypair_name = KEYPAIR_NAME
		aws.region = "us-west-2"
		aws.ami = "ami-02701bcdc5509e57b" #Ubuntu Server 18.04
		aws.instance_type = "t2.nano"
		aws.security_groups = ["vagrant"]
		aws.elastic_ip = "34.215.194.24"
		override.vm.synced_folder ".", "/vagrant", disabled: true
		override.ssh.username = "ubuntu"
		override.ssh.private_key_path = "~/it115.pem"		
  
	end

	config.vm.define "wildwest" do |wildwest|
		config.vm.provision "ansible" do |ansible|
			ansible.extra_vars = { ansible_python_interpreter:"/usr/bin/python3" }
			ansible.playbook = "wildwest.yml"
			ansible.verbose = "v"
		end
	end
	
	
end