#lxd-exploration

I want to learn more about lxd. For now this is a basic setup to allow me to play around with things on MacOS via a VM stood up by Vagrant.

- To get things going, run `vagrant up`. 
- Once everything is good to go, add the box as the remote by running `lxc remote add localhost` and using the password `password` (this is for _local_ lxd exploration, never use a password like this in any other env). 
- Set the VM as your default remote by running `lxc remote switch localhost`.
- Get a minimal image up with `lxc launch images:alpine/3.4 first`.
