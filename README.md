# Vagrant box with minikube installed using Centos 7 official Vagrant box

# Windows (Tested in Windows 10 Pro)

    Requirements

        - Hyper-V enabled or Virtualbox
        - Vagrant

# MacOS

    Requirements

        - Virtualbox
        - Vagrant

# Vagrant commands

    Run

        vagrant up --provider hyperv (Windows)
        vagrant up --provider virtualbox (MacOS or Windows)  

    Access the VM

        vagrant ssh           

    Delete

        vagrant destroy


# Installing specific minikube version

    Check the Vagrantfile, ansible_local provision section, extra_vars. 

# Installing more than one VM

    You can add more VM in the Vagrantfile using the servers array:

    Example:

        servers=[
            {
                :hostname => "minikube-demo1",
                :memory => "4096",
		        :cpu => "4"
            },
            {
                :hostname => "minikube-demo2",
                :memory => "8192",
		        :cpu => "2"
            }
        ]   

    To access an specific vm refer to the hostname for example: vagrant ssh minikube-demo1         

# Notes

    Thanks to:

        https://github.com/mrvantage/vagrant-box-centos7-minikube (for the ansible playbook)

