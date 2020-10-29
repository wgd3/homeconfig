# Infrastructure

This directory contains the files necessary for running `ansible-playbook` against known hosts in my home lab

### Set Up

It is assumed (before running `ansible-playbook`) that the following are true:

- User has been added/exists on host
- User has the home lab public RSA key added to their `authorized_keys` file
- User has `sudo` privileges without requiring a password

### Common Role

WIP

### Docker Role

WIP

### Home Automation Role

This role is assigned to one (or more, but not in my case ) servers that will run HomeBridge, HomeAssistant, and Grafana. In this lab a Raspberry Pi 4 B 2GB is used as the host, and some of the tasks are conditional on which distribution is running on the Pi. Raspbian is used on these Pi's, and so the HomeAssistant image is set to the `homeassistant/raspberrypi4-homeassistant` image.

This role also bases everything out of a `/opt/home_automation` directory on the host. This folder can be configured in `vars/main.yml`. Since it is assumed that at least 2 users exist on the hose (root and the user created prior to running this playbook), and both belong to the `sudo` group, this base directory is created with 0664 permissions (recursively) and group ownership is set to `sudo`. This allows your normal user (that has sudo access) to also use it's UID and GID to spin up containers, and write to all the sub-directories.
