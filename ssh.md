# Use ssh command to create tunnel

Source: http://pixelsvsbytes.com/blog/2011/09/easy-ssh-tunnelling-for-the-mac/

```
ssh -N -C -D <port> <ip_address>
```

The `-N` option means no interactive shell. The `-C` turns on compression.

## SSH tunnel script

Create a shell script to start the tunnel.

```bash
nano ~/bin/tunnel.sh
chmod u+x ~/bin/tunnel.sh
```

Sample code:

```bash
PORT=10134
echo "Starting ssh tunnel on port $PORT"
ssh -N -C -D $PORT 132.200.90.101
```

## Testing

Visit ipecho.net and note what IP address you currently have.

```
curl http://ipecho.net/plain
```

Now see what IP address you get when you tunnel through the proxy.

```
curl -s --proxy socks5://127.0.0.1:<port> http://ipecho.net/plain
```
