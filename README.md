# Alternative Cost Reduction Approach : Vagrant Using Virtualbox and Ansible

The Vagrant Ansible provisioner allows you to provision the guest using Ansible playbooks by executing ansible-playbook from the Vagrant host.

## Setup Requirement
If installing Ansible directly on the Vagrant host is not an option in your development environment, you might be looking for the [Ansible Local provisioner](https://www.vagrantup.com/docs/provisioning/ansible_local.html) alternative

### Assignment Requirements

- Create an ec2 Linux web node

- Use Ansible to install:
    - HTTP Server

- Optional : Create 2 ec2 web nodes and add ELB at the front as a reverse proxy

### Additional notes:

- Setup the Linux box so that you can SSH into it using your SSH key
- Document your approach, your design and what would you have done differently if you had more time
- Code should be checked into a git repository. Please share your repository with us.


### Essential Plugin For Cloud Deployment Includes:

- Install vagrant-aws plugin 
```
vagrant plugin install vagrant-aws
```
- Install vagrant-azure plugin 
```
vagrant plugin install vagrant-azure
```
- Install vagrant-google plugin 
```
vagrant plugin install vagrant-google
```
- Install vagrant-digitalocean plugin 
```
vagrant plugin install vagrant-digitalocean
```

### For AWS:

- Install the AWS CLI in a vagrant host as it will help to retrieve certain information that is needed to create our machine. Use a recent version of pip and just run:
```
pip install aws-cli
```
- Use *Vagrant-AWS* plugin that adds AWS provider to Vagrant to control and provision machines in Amazon Web Services.

### For Azure:

- Install the Azure CLI in a vagrant host as it will help to retrieve certain information that is needed to create our machine. If a recent version of Node.js is installed, just run:
```
npm install -g azure-cli
```

- Use *Vagrant-Azure* plugin that adds Microsoft Azure provider to Vagrant to control and provision machines in Microsoft Azure.

### Running The Solution

- Add a dummy AWS vagrant image
```
vagrant box add aws-dummy https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box
```

- Start a vagrantbox with
```
vagrant up --provider=aws
```

- To configure the vagrantbox modify the Ansible Playbook and apply changes with
```
vagrant provision
```

## Built With

* [VirtualBox](https://www.virtualbox.org/) - VirtualBox VMs
* [Vagrant](https://www.vagrantup.com/intro/getting-started/providers.html) - About Vagrant Providers
* [Vagrant-AWS](https://github.com/mitchellh/vagrant-aws) - AWS Provisioning
* [Vagrant-Azure](https://github.com/Azure/vagrant-azure) - Azure Provisioning
* [Vagrant-Google](https://github.com/mitchellh/vagrant-google) - Google Cloud Provisioning
* [Ansible](https://docs.ansible.com/ansible/latest/scenario_guides/guide_aws.html) - Environment Orchestration Tool

## Authors

* **Gerald Luzangi** - [gluzangi](https://github.com/gluzangi)


## Acknowledgments

* Hat tip to KIRASYSTEMS.com for Inspiration