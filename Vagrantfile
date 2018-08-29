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
        aws.region = ENV['AWS_AVAILABILITY_ZONE']
        aws.ami = 'ami-0c7d8678e345b414c'
        aws.instance_type = 't3.nano'
        aws.subnet_id = ENV['AWS_SUBNET_ID']
        aws.security_groups = ENV['AWS_SECURITY_GROUP']
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
