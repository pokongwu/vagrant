# Vagrant

- Website: [https://www.vagrantup.com/](https://www.vagrantup.com/)
- Source: [https://github.com/hashicorp/vagrant](https://github.com/hashicorp/vagrant)
- HashiCorp Discuss: [https://discuss.hashicorp.com/c/vagrant/24](https://discuss.hashicorp.com/c/vagrant/24)

Vagrant is a tool for building and distributing development environments.

Development environments managed by Vagrant can run on local virtualized
platforms such as VirtualBox or VMware, in the cloud via AWS or OpenStack,
or in containers such as with Docker or raw LXC.

Vagrant provides the framework and configuration format to create and
manage complete portable development environments. These development
environments can live on your computer or in the cloud, and are portable
between Windows, Mac OS X, and Linux.

## To Start
Navigate into the vagrant folder :

`cd vagrant/`
`vagrant up`


Note: `vagrant up` will build the grant file that is already existing inside this folder.
if you want to adjust the CPU or Provisioning , you can do so by 'nano Vagrantfile' to edit the file.

In our case we provisioned the virtual machine start with a website running on it.

## Provisioning

```bash

config.vm.provision "shell", inline: <<-SHELL
     yum install httpd wget unzip vim -y
     systemctl start httpd
     systemctl enabled httpd
     mkdir -p /tmp/finance
     cd /tmp/finance
     wget https://www.tooplate.com/zip-templates/2135_mini_finance.zip
     unzip -o 2135_mini_finance.zip
     cp -r 2135_mini_finance/* /var/www/html/
     systemctl restart httpd
     cd /tmp/
     rm -rf /tmp/finance
   SHELL

```
## To learn more

To learn how to build a fully functional development environment, follow the
[getting started guide](https://www.vagrantup.com/docs/getting-started).