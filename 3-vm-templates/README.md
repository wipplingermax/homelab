# VM Templates
For fast deployment of VMs, templates are used.
Templates can be used to automate tedious installation and configuration procedures.

Templates have big advantages over cloning a VM: 
users, network address and many other settings can be customized.

Futhermore Templates are highly customizeable and thus tailorized to specific needs. 

**Tech-Stack used to create Templates**
- **packer:** CLI-Tool to create custom images from template-files 
- **cloud-init:** industry standard multi-distribution method for cross-platform cloud instance initialisation - so: fill custom images with custom configuration settings (user, network, ssh-keys...)

## Creating custom Templates with packer

### 1. Install packer on Linux

Add GPG Key
```
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
```

Add Repo
```
sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
```

Update and install
```
sudo apt-get update && sudo apt-get install packer
```

For different OS or more Information [click here](https://developer.hashicorp.com/packer/tutorials/docker-get-started/get-started-install-cli) 

### 2. Create template config

- create folder for new template 
- create pkr.hcl-config and http/file-configs
- validate configuration
```
packer validate -var-file="../credentials.pkr.hcl" "TEMPLATE_NAME.pkr.hcl"
```


### 3. Use packer to create proxmox-template

build template
```
packer validate -var-file="../credentials.pkr.hcl" "TEMPLATE_NAME.pkr.hcl"
```


