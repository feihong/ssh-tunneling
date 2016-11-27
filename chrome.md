# Use Proxy through Chrome

```
/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --proxy-server="socks5://localhost:15600" --host-resolver-rules="MAP * 0.0.0.0 , EXCLUDE localhost"
```

## Sources

- [Configuring a SOCKS proxy server in Chrome](https://www.chromium.org/developers/design-documents/network-stack/socks-proxy)
- [How to specify command line flags](https://www.chromium.org/for-testers/command-line-flags)
