# Use Proxy through Chrome

```
/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --proxy-server="socks5://localhost:15600" --host-resolver-rules="MAP * 0.0.0.0 , EXCLUDE localhost"
```

## Notes

The command line options only take effect if you run the command while there is no Chrome process already open. If Chrome is already open, then running the command only opens a new window for the current process, which will not use the proxy settings you specified on the command line.

For some reason, I'm unable to create a symbolic link for running Chrome on Mac OS X.

## Sources

- [Configuring a SOCKS proxy server in Chrome](https://www.chromium.org/developers/design-documents/network-stack/socks-proxy)
- [How to specify command line flags](https://www.chromium.org/for-testers/command-line-flags)
