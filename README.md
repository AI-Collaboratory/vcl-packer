# VCL Ubuntu Machine Packer
This is a project that builds the basic desktop image for the UMD iSchool's Virtual Computer Lab hosted in Amazon's EC2 service. We use Packer.io and Ansible to create an Ubuntu desktop Amazon machine image (AMI) with certain features.

* VNC and RDP for remote desktop
* Shared remote desktops (same session)
* Default user of "dcic" with password
* Autologin to desktop
* Turn off autohide of menu
* Startup applications:
 * terminal (with greeting)
 * nautilus (file browser)

The images created by this tool are used as base AMIs for similar builders, which then add custom software for specific courses and labs. This two-step approach saves time and bandwidth.

## Local Dependencies
You will need the following software to run the builder:
* Packer.io installed and configured on PATH (see http://packer.io).

## Building Images
There are a few files you need to get started, beyond this project:
* hosts - can be an empty file
* group_vars/vcl
 - dcic_password and dcic_password_crypt variables

You can put these files or folders in any local directory, but you will need to edit template.json to match their location.

You also need a standard AWS credentials file, located at ~/.aws/credentials. The Packer amazon-ebs builder will pick them up there.

The command to build the image is:

    $ packer build template.json
