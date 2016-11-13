# SSH Tunneling HOWTO

Instructions for setting up SSH tunneling on a DigitalOcean droplet.

## Creating the droplet on DigitalOcean

1. Click `Create Droplet`
1. Select Ubuntu 16.04 x64
1. Select $5/mo
1. Select Singapore
1. Give it a hostname of 'tunnel' (or whatever you prefer)

## Adding your user

After your droplet has been created, you will receive an email informing you of its IP address and root password. SSH into your droplet:

```bash
ssh root@<ip_address>
```

Note that the first time you log in, you will be forced to change the password. If you set everything up correctly, though, you'll never have to use the root password again. However, if you need to make future changes you can always reset the root password in the Access section of the droplet control panel page.

Add a new user named `bobby`:

```bash
adduser bobby
```

Add your SSH public key:

```bash
cd /home/bobby
mkdir .ssh
cd .ssh
nano authorized_keys   # copy text from ~/.ssh/id_rsa.pub
chmod 600 authorized_keys
chown bobby:bobby authorized_keys
```

## Testing

Start an SSH tunnel on port 15600:

```
ssh -NC -D 15600 bobby@<ip_address>
```

Visit ipecho.net and note what IP address you currently have.

```
curl http://ipecho.net/plain
```

Now see what IP address you get when you tunnel through the proxy.

```
curl -s --proxy socks5://127.0.0.1:15600 http://ipecho.net/plain
```

## Notes

Source: [How To Route Web Traffic Securely Without a VPN Using a SOCKS Tunnel](https://www.digitalocean.com/community/tutorials/how-to-route-web-traffic-securely-without-a-vpn-using-a-socks-tunnel)

## License

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
