# Installation

Since this utility uses Ruby, and we're a Windows shop, it's recommended that you use Vagrant + VirtualBox to run this generator.

1. Install VirtualBox: https://www.virtualbox.org/wiki/Downloads
2. Install Vagrant: https://www.vagrantup.com/downloads.html
3. Clone this repo
4. Open a terminal window and browse to the location where you cloned this repo
5. Edit line 18 of `Vagrantfile` to update the path to your "PlatformSync" documentation repo.  Take care to include the trailing `/docs`.  Also, escape backslashes with an additional backslash.  Resulting string should look like: `config.vm.synced_folder "C:\\Users\\awagner\\Documents\\github\\PlatformSync\\docs", "/vagrant/build"`
6. Type `vagrant up` to start the VM
7. Edit the files in `/source` at will, and the files will be rebuilt upon save

> Vagrant is helpful here because this is a site generator based on the Ruby language.  This keeps authoring the documentation simple and predictable.  However, installing Ruby on Windows is an exercise in futility.  Virtualbox + Vagrant will start up a VM with everything on it that you need.  

# Reference

https://github.com/lord/slate/wiki

# Deploying Docs

Deploying is semi-straightforward.  To do so:
1. Open a terminal window and browse to the location where you cloned this repo
2. Connect to the Vagrant Box by typing in `vagrant ssh` from the 
3. Type `cd /vagrant` and hit enter
4. Type `bundle exec middleman build --clean` and hit enter

This will create a build of the files and output them to the `docs` folder of the PlatformSync repo.  From there, push those changes and the docs site should be automatically updated.