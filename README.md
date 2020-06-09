# terraform

Download and install HashiCorp Terraform and associated plugins. 
https://www.terraform.io/guides/running-terraform-in-automation.html#pre-installed-plugins

For information about PTA and how to use it with this Ansible role please visit https://github.com/Forcepoint/fp-pta-overview/blob/master/README.md

## Requirements

None

## Role Variables

### REQUIRED

None

### OPTIONAL

* terraform_version: The version of Terraform to install.
* terraform_checksum: The checksum for the Terraform binaries.
* terraform_download_url: The URL to download Terraform plugins from.
  Useful if you want to access the Hashicorp site through a proxy like an Artifactory remote repository.
* terraform_plugins_dest: A local folder that the specified plugins are downloaded to. Again, useful if
  you cannot reach the Terraform site directly and wish to install/use the plugins locally.
* terraform_plugins: The desired terraform plugins and their versions. See the example for proper syntax.
  The only real reason you'd want to specify these is if you might ever need to run a terraform init while offline.

## Dependencies

None

## Example Playbook

    - hosts: terraform
      vars:
        terraform_version: 0.11.7
        terraform_checksum: sha256:6b8ce67647a59b2a3f70199c304abca0ddec0e49fd060944c26f666298e23418
        terraform_download_url: https://artifactory.COMPANY.com/artifactory/releases.hashicorp.com
        terraform_plugins_dest: /usr/lib/custom-terraform-plugins
        terraform_plugins:
          - { name: terraform-provider-vsphere, version: 1.6.0 }
          - { name: terraform-provider-null, version: 1.0.0 }
      roles:
         - role: terraform

## License

BSD-3-Clause

# Author Information

Jeremy Cornett <jeremy.cornett@forcepoint.com>
