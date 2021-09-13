# Shadowsocks(R)/V2Ray subscription decoder/parser

A 100-line POSIX compatible shell script to decode, parse Shadowsocks(R)/V2Ray subscription link and create configuration files.

**Disclaimer:** This is a toy project. I don't know the standard of the encoding of those link URLs, so some parsing could quite possibly go wrong.

## Requirement:

- `base64` to decode base64 format data
- `curl` or `wget` to download a link, optional if a base64 encoded link is provided

## Usage

The script accepts either one CLI argument or multiple from pipe. The arguments can be one or more of:
- A single `ss://` or `ssr://` or `vmess://` link. This contains a single configuration.
- A `http(s)://` subscription link. This normally contains multiple configurations.
- A base64 encoded string downloaded from a `http(s)` subscription link.

```
ssr-decode [ http(s)://link | ss(r)://BASE64 | vmess://BASE64 | BASE64 | < input.txt ]
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
