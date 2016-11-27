# SSH tunneling on Windows

## Installation

You need to download and install the [plink](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) program. This is the Windows equivalent of the Unix `ssh` command.

## Create tunnel

```
plink -ssh -D 15600 -C -T -N -i <private_key_file> <user>@<ip_adddress>
```

-D specifies the port on localhost that you should point your browser at  
-C means turn on compression  
-T means don't open interactive shell on remote server  
-N means don't start shell  
-i specifies the private key file  

Note that the private key file needs to be a .ppk file accepted by PuTTY. If you have a private key file from Unix, you can convert it using the [puttygen](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) program.

## Testing

The `curl` command can be installed by running `choco install curl`.

```
curl.exe http://ipecho.net/plain
curl.exe -s --proxy socks5://127.0.0.1:15600 http://ipecho.net/plain
```

## Source

[Creating Dynamic SSH Tunnel on Windows with Plink](http://www.pc-freak.net/blog/creating-ssh-tunnel-windows-plink/)
