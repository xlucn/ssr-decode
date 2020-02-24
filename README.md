# Shadowsocks(R) subscription decoder/parser

A POSIX compatible shell script to decode and parse Shadowsocks/ShadowsocksR subscription link.

## Usage

The script accepts input as one argument or from pipe. The argument can be:
- `http(s)://` protocol subscription link (normally contains multiple configs)
- A single `ss://` or `ssr://` protocol link
- The downloaded content of subscription link (base64 encoded)

```sh
sh ss-subs [ https://link | ss://BASE64 | ssr://BASE64 | BASE64 | < input.txt ]
```

The script will generate `.json` configuration files for each Shadowsocks(R) setup. The ShadowsocksR configuration file will be named to `ssr-$group-$remarks.json` with `group` normally being the service provider, `remarks` being the description of this setup. The Shadowsocks configuration file will be named to `ss-$server-$port.json`.
