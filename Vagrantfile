# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

    # Specify the box in use.
    config.vm.box = "wplib/wplib"

    # Set up a private network with a specific IP address.
    #
    # This NEEDS to be changed if you run multiple instances of the box concurrently.
    config.vm.network "private_network", ip: "192.168.33.10"

    # Set the hostname for the box.
    #
    # The host OS' hosts file will be updated if you have installed the
    # hostsupdater vagrant plugin. This allows you to type 'wplib.box' into
    # the browser on your host machine and access the virtual machine.
    #
    # This should be changed to match your site: e.g. dev.example.com.
    config.vm.hostname = "wplib.box"

    # Mount the host OS www folder inside the virtual machine's webroot directory.
    config.vm.synced_folder "www", "/var/www"

    # Allow the host machine user's ssh key to be forwarded to the virtual machine.
    # See: https://developer.github.com/guides/using-ssh-agent-forwarding/
    config.ssh.forward_agent = true

    # Always use the published key for vagrant user.
    # See: https://github.com/mitchellh/vagrant/tree/master/keys
    config.ssh.insert_key = false

    # Run a shell script on the first `vagrant up` (and when the --provision flag is specified)
    # to import the default database and ensure the link for the object cache drop in.
    config.vm.provision "shell", path: "scripts/provision.sh"

end
