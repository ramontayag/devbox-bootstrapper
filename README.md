Generic dev box

## Preparation

Copy the config:

```
cp box.yml{.sample,}
```

Edit the `box.yml` to pick your own settings for the virtual machine. `vagrant up` to start the VM.

Change ubuntu's password:

```
vagrant ssh
sudo passwd ubuntu
```

Use the password `ubuntu`, then `exit`.

```
ssh-add /path/to/your/private_key
ssh-copy-id -i /path/to/your/public_key.pub ubuntu@ip.of.vagrant.box
```

If you still can't run the playbooks below, `vagrant ssh` and edit the `~/.ssh/authorized_keys`. I've seen instances where your public key was not properly appended. You can fix it manually.

Install the guest additions plugin in the host:

```
vagrant plugin install vagrant-vbguest
```

## Hosts file

Copy `hosts.sample` to `hosts`:

```
cp hosts{.sample,}
```

Then edit the file to point to the IP of the virtual machine. Later, when running the playbooks, we will specify what group to use.

## Running Playbooks

All of the playbooks below are run like this:

```
ansible-playbook <playbook-name>.yml -i hosts -l <virtualbox or digitalocean>
```

## Bootstrap the box for ansible

```
vagrant ssh
sudo apt-get update
sudo apt-get install ansible
```

### Setup

This should always be run.

Playbook name: `setup`

### PostgreSQL

Playbook name: `postgresql`

Make sure your `group_vars/development` the following settings:

```
postgresql_password: XXXXXXXXXX
postgresql_databases:
  - app_testdb
  - app_devdb
```

### Ember

Playbook name: `ember`

### Ruby

Playbook name: `ruby`. This installs RVM.
