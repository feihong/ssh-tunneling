# ssh-tunneling

Instructions for setting up SSH tunneling on a DigitalOcean droplet.

## Creating the droplet on DigitalOcean

1. Click `Create Droplet`
2. Name it 'tunnel'
2. Select $5/mo
3. Select Singapore
4. Select Ubuntu 16.04
5. Add your SSH key (probably already there if you've created other droplets)

## Adding your user

```bash
adduser username
visudo
```

Add this line: `username ALL=(ALL:ALL) ALL`

```bash
cd /home/username
mkdir .ssh
cd .ssh
nano authorized_keys   # copy in the keys
chmod 600 authorized_keys
chown username:username authorized_keys
```

Remember that you can always reset your root password in the control panel.

## License

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
