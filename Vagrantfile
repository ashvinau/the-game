Vagrant.configure("2") do |config|
config.vm.box = "dummy"

	config.vm.provider :aws do |aws, override|
    
		aws.access_key_id = "AKIA3FXPI52PARRK2C4F"
		aws.secret_access_key = "Q55MO0+rV+ZLAJUed0rwFI6cKFdEFmHdlYJ4IePO"
		aws.keypair_name = "it115"
		aws.region = "us-west-2"
		aws.ami = "ami-02701bcdc5509e57b" #Ubuntu Server 18.04
		aws.instance_type = "t2.nano"
		aws.security_groups = ["vagrant"]
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