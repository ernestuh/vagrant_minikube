# Vagrant minikube VM

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

    Delete

        vagrant destroy

# Installing specific minikube version

    Check the Vagrantfile, ansible_local provision section, extra_vars. 

# Notes

    Thanks to:

        https://github.com/mrvantage/vagrant-box-centos7-minikube (for the ansible playbook)

