This is an unofficial guide for installing CARTO in a Vagrant VM. It's useful for development, hiring tests (take a look at [CARTO open positions](https://carto.com/jobs))... It deals with subtle differences with Ubuntu distributions and Vagrant specifics.

# Prerequisite

Install [Vagrant](https://www.vagrantup.com/intro/getting-started/install.html). This has been tested with Vagrant 1.9.1 and VirtualBox 5.1.22.

# Installing CARTO

Next steps take ~1:30 hour, mostly downloading and compiling the whole Internet. Twice.

Some commands, such as `vagrant up` or `npm install`, take a while.

## Prepare a VM

This set ups a Vagrant VM with Ubuntu 12 and ssh into it:

```bash
vagrant up
vagrant ssh
sudo apt-get update
sudo apt-get install vim
```

## Install CARTO

Previous notes:
- I'd suggest you to go to your home `cd ~` before every `git clone`.
- Before running `node app.js development` for Node servers, do this:
  - For SQL API you must edit `config/environments/development.js` and set `module.exports.node_host` to `0.0.0.0`.
  - For Windshaft you must edit `config/environments/development.js` and set `config.host` to `0.0.0.0`. 
- You'll be prompted for the password on `bundle install`. It's `vagrant`.

Follow [CARTO installation guide](http://cartodb.readthedocs.io/en/latest/install.html).

## Create a user

[Create a user](http://cartodb.readthedocs.io/en/latest/operations/create_users.html).

Add your user to `/etc/hosts`:

```
127.0.0.1       juanignaciosl.localhost.lan
```

Afterwards, you'll be able to login at http://localhost.lan:3000/login with your new user.
