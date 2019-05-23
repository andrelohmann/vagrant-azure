# vagrant-azure - (c) Andre Lohmann (and others) 2019

## Maintainer Contact
 * Andre Lohmann
   <lohmann.andre (at) gmail (dot) com>

## content

Vagrant machine, to deploy IaC Stacks using Terrafrom and the [terrahelper](https://github.com/andrelohmann/ansible-role-terrahelper) best practice on Azure.

## Usage

### Requirements

  * Azure Service Principal
  * Terraform Template repository
  * Terraform State repository
  * Private/Public key for the programmatic repository access

### Access the azure cloud

To access the azure cloud programmatically using the cli, you need to create a subscription and a service principal. Just follow the following documentation, to put everything in place.

https://docs.microsoft.com/de-de/azure/active-directory/develop/howto-create-service-principal-portal

After you folowed all the steps and created the service principal, write down the credentials.

  * Tennent ID/Directory ID (two names for the same thing)
  * Subscription ID
  * Application ID
  * Application Key (you created this one)

### Configuration

Copy the config.yml.example to config.yml and alternate as you need it.

Copy your private key to ansible/files/private_keys.

Copy ansible/custom_vars.yml.example to ansible/custom_vars.yml and alternate as you need it.

### Run

```
vagrant up
```

```
vagrant ssh
```

From within the vagrant machine, you will find two directories (/home/vagrant/terraform and /home/vagrant/terraform_state). These are your Terraform repositories, that are mapped to the same named directories on your host machine (inside the vagrant project folder).

Access the terraform directory from within your vagrant machine and use one of the following aliases, to run the terraform commands:

```
tfi
```
to initialize the terraform templates folder (download plugins and providers)

```
tfp
```
to run the validation and plan phase

```
tfa
```
to run the apply phase (rollout the stack on your azure subscription)

```
tfp
```
to destroy the azure stack (delete all resources on azure)
