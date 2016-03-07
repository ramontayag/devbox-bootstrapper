Generic dev box

## Preparation

Copy the config:

```
cp box.yml{.sample,}
```

Edit the `box.yml` to pick your own settings for the virtual machine. `vagrant up` to start the VM.

```
ssh-add /path/to/your/private_key
ssh-copy-id -i /path/to/your/public_key.pub vagrant@ip.of.vagrant.box
```

`vagrant` user's password is `vagrant`.

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

### Setup

This should always be run.

Playbook name: `setup`

### PostgreSQL

Playbook name: `postgresql`

Make sure your `group_vars/development` the following settings:

```
postgresql_password:
  - XXXXXXXXXX
postgresql_databases:
  - app_testdb
  - app_devdb
```

### Ember

Playbook name: `ember`

### Ruby

Playbook name: `ruby`. This installs RVM.

### PostgreSQL

Playbook name: `postgresql`

Requires the following to be set in the group vars:

```
postgresql_databases:
  - an_app_database
postgresql_password:
  - SOMEPASSWORD
```
