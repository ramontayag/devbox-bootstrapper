Ubuntu 19.04 devbox setup

## Preparation

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

### Google Chrome

Playbook name: `google-chrome-stable`

Installs google-chrome-stable for headless tests

### Ember

Playbook name: `ember`

### Ruby

Playbook name: `ruby`. This installs RVM.

### Docker

Playbook name: `docker`

### Shutdown if Idle

Playbook name: `auto_shutdown`

Shuts down the computer if idle for 30 seconds.