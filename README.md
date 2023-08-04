# Workstation Bootstrap

This playbook will bootstrap your VM for working with ansible and a few other things
at DST.

Supported Operating Systems:

* Ubuntu 23.04

## Usage

**Pre-requisites**

* git
* ansible (system install will be removed by playbook after installing latest version)

Below is the basic usage and will get you started.

    ansible-pull -U https://github.com/dstdev/workstation-bootstrap -K

Notes:
* If you have passwordless sudo enabled, run without the `-K`

## What this playbook does

* Installs the following packages:
    * ansible
    * awscli
    * curl
    * docker
    * filezilla
    * git
    * globalprotect-openconnect
    * htop
    * molecule
    * neovim
    * nmap
    * openconnect
    * pipx
    * pre-commit
    * rsync
    * sshfs
    * terraform
    * tmux
    * vim
    * wget
    * vscode
    * bitwarden
* Installs the following vscode extensions
    * redhat.ansible
    * redhat.vscode-yaml
    * dhoeric.ansible-vault
    * GitHub.remotehub
    * jdinhlife.gruvbox
    * HashiCorp.terraform
    * ms-python.python
    * golang.Go
* Configures Git
* Configures SSH Client

## Adding reuseable variables

If you want to shorten the execution of the above and get your git and vim settings initialized, you can create
a yaml file with those variables and call it directly

    # Set in vars.yaml
    git_email: andrew.a.kail@gmail.com
    git_name: "Andrew Kail"
    enable_vim: true

Then reference the file when executing ansible-pull.

    ansible-pull -U https://github.com/dstdev/workstation-bootstrap -K -e "@vars.yaml"


This file can be kept separate from the repo and reused on other VMS.

## Configuration Variables

The following configurations can be set using vars.yaml above.  By default
these variables are set to false and the playbook will still run without them.
However it will be recommended to configure these for more effective usage.

| Variable | Description |
| --- | --- |
| enable_vim | Install vim extension in vscode |
| git_email | Email to identify you with git commits. Required for pushing to github |
| git_name | Nice name identify you with git commits. Required for pushing to github |
| ssh_rsa_private_key | Contents of rsa private  key |
| ssh_rsa_public_key | Contents of rsa public key |
| ssh_ed25519_private_key | Contents of ed25519 private key (Generated automatically if blank|
| ssh_ed25519_public_key | Contents of ed25519 public key |