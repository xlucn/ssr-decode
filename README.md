# Shadowsocks(R)/V2Ray subscription decoder/parser

A POSIX compatible shell script to decode and parse Shadowsocks(R)/V2Ray subscription link.

**Disclaimer:** This is a toy project. I don't know the standard of those link URL, so some parsing could quite possibly go wrong.

## Requirement:

- `curl` or `wget` to download a link, optional if a base64 encoded link is provided
- `base64` to decode base64 format data

## Usage

The script accepts either one CLI argument or multiple from pipe. The arguments can be:
- `http(s)://` protocol subscription link which normally contains multiple configurations
- A single `ss://` or `ssr://` or `vmess://` protocol link which is a single configuration
- The downloaded content of subscription link (base64 encoded)

```sh
ssr-decode [ (http|https)://link | (ss|ssr|vmess)://BASE64 | BASE64 | < input.txt ]
```

### Customization

The `local_port` and `timeout` in the shadowsocks settings can be controlled with environment variables by `LOCAL_PORT` and `TIMEOUT`, the default is 1080 for local port and 300 for timeout

```sh
LOCAL_PORT=1234 TIMEOUT=600 ssr-decode
```

## Output

The script will generate `*.json` configuration files for each Shadowsocks(R)/V2Ray setup.

- The ShadowsocksR configuration file will be named `ssr-$group-$remarks.json` with `group` normally being the service provider, `remarks` being the description of this setup.
- The Shadowsocks configuration file will be named `ss-$server-$port.json`.
- The V2Ray configuration file will be named `v2ray-$ps.json` with `ps` normally being the description.
