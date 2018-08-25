# -*- mode: ruby -*-
# vi: set ft=ruby :
# create and configure the AWS instance(s)
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config| 

    # use dummy AWS box
    config.vm.box = 'aws-dummy'

    # specify AWS provider configuration
    config.vm.provider :aws do |aws, override|
        # read AWS authentication information from environment variables
        aws.access_key_id = ENV['AWS_ACCESS_KEY_ID']
        aws.secret_access_key = ENV['AWS_SECRET_ACCESS_KEY']

        # specify SSH keypair to use
        aws.keypair_name = ENV['AWS_KEYPAIR_NAME']

        # specify region, AMI ID, and security group(s)
        aws.region = 'us-east-1'
        aws.ami = 'ami-0e9fd1c836b42538e'
        aws.instance_type = 't3.nano'
        aws.subnet_id = 'subnet-15b52570'
        aws.security_groups = 'sg-00726a0897aae5445'
        aws.associate_public_ip = 'true'

        # specify username and private key path
        override.ssh.username = 'ec2-user'
        override.ssh.private_key_path = '~/.ssh/id_rsa'

        config.vm.provision :ansible do |ansible|
            ansible.verbose = "v"
            ansible.playbook = "playbook.yml"
        end
    end
end
