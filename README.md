# Shadowsocks(R)/V2Ray subscription decoder/parser

A POSIX compatible shell script to decode and parse Shadowsocks/ShadowsocksR/V2Ray subscription link.

## Usage

The script accepts input as one CLI argument or multiple from pipe. The argument can be:
- `http(s)://` protocol subscription link (normally contains multiple configs)
- A single `ss://` or `ssr://` or `vmess://` protocol link
- The downloaded content of subscription link (base64 encoded)

```sh
sh ss-subs [ https://link | (ss|ssr|vmess)://BASE64 | BASE64 | < input.txt ]
```

The script will generate `.json` configuration files for each Shadowsocks(R)/V2Ray setup. The ShadowsocksR configuration file will be named to `ssr-$group-$remarks.json` with `group` normally being the service provider, `remarks` being the description of this setup. The Shadowsocks configuration file will be named to `ss-$server-$port.json`. The V2Ray configuration file will be named to `v2ray-$ps.json` with `ps` normally being the description.
