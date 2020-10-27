# Infrastructure

This directory contains the files necessary for running `ansible-playbook` against known hosts in my home lab

### Set Up

It is assumed (before running `ansible-playbook`) that the following are true:

- User has been added/exists on host
- User has the home lab public RSA key added to their `authorized_keys` file
- User has `sudo` privileges without requiring a password
