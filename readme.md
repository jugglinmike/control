# Control

My personal setup for deploying web applications to a VPS.

## Requirements

- [Python](https://www.python.org/) 2.7 or higher
- Python modules:
  - [Passlib](http://pythonhosted.org/passlib/)
  - [Ansible](http://ansible.com)
- [Vagrant](http://vagrantup.com) (for development)

## Running

Setup is divided into two steps:

1. **Hardening.** This disables root login, so it may only be run once in order
   to configure the remote machine.
2. **Provisioning.** The provisioning step. This configures the system with all
   necessary settings and software dependencies. This executes as the remote
   user created in the previous step.

### Step 1

For local testing, run the command:

    $ vagrant up

For working with remote machines, run the command:

    $ ansible-playbook deploy/01-harden.yml -i deploy/inventory/{{ remote inventory file name here }}

### Step 2

Execute the following command:

    $ ansible-playbook deploy/02-provision.yml -i deploy/inventory/{{ remote inventory file name here }}
