Ubuntu 19.10 devbox setup

## Preparation

Copy the config:

```
cp box.yml{.sample,}
```

The section on running playbooks below assumes you can already connect to your machine remotely.

## Hosts file

Copy `hosts.sample` to `hosts`:

```
cp hosts{.sample,}
```

Edit the file to point to the IP of the virtual machine. Later, when running the playbooks, we will specify what group to use.

## Running Playbooks

All of the playbooks below are run like this:

```
ansible-playbook <playbook-name>.yml -i hosts
```

### Setup

This should always be run.

Playbook name: `setup`

### Ember

Playbook name: `ember`

### Ruby

Playbook name: `ruby`. This installs RVM.

### Docker

Playbook name: `docker`
