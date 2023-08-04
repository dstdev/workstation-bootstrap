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

## Adding reuseable variables

If you want to shorten the execution of the above and get your git and vim settings initialized, you can create
a yaml file with those variables and call it directly

    # Set in vars.yaml
    git_email: andrew.a.kail@gmail.com
    git_name: "Andrew Kail"
    enable_vim: true

Then reference the file when executing ansible-pull.

    ansible-pull -U https://github.com/dstdev/workstation-bootstrap -K -e "@vars.yaml"

## Configuration Variables

| Variable | Description |
| --- | --- |
| enable_vim | Install vim extension in vscode |
| git_email | Email to identify you with git commits. Required for pushing to github |
| git_name | Nice name identify you with git commits. Required for pushing to github |
| ssh_rsa_private_key | |
| ssh_rsa_public_key | |
| ssh_ed25519_private_key | |
| ssh_ed25519_public_key | |