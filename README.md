# Vultr hook script for [Dehydrated](https://dehydrated.de)

This hook script for [Dehydrated](https://dehydrated.de) enables the dns-01 verification
using the [Vultr](https://vultr.com) DNS service.

## Dependencies

This script is only tested in Bash and requires:

- curl
- jq

For a Ubuntu/Debian based Linux system:

```bash
$ sudo apt install curl jq
```

## Configuration

Request an API key from the Vultr web interface and create a configuration
file as ```/etc/dehydrated/vultr.inc```. It should look like the following:

```bash
APIKEY="XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
```

## Usage

This script can be used in two ways:

### Stand-alone

Set this script as your HOOK script in Dehydrated.

### Combining multiple hooks

Since the Vultr DNS service only allows for verification it only acts on the
```deploy_challenge``` and ```clean_challenge``` hooks. To deploy your 
certificates you will need another script that does that.

Read [Example: Using multiple hooks](https://github.com/lukas2511/dehydrated/wiki/Example:-Using-multiple-hooks)
on how to do this.

A nice example would be the [dehydrated-vault-hook](https://github.com/ttalle/dehydrated-vault-hook) script that stores
the certificate, chain and key as a secret in Vault. This enables services
to safely retreive their certificates themselves.

## Warning/Disclaimer/Current status

There is not much error checking at the moment. Use at your own risk. I advise to use the Let's Encrypt
staging servers while testing this script to avoid running into the limits.

## Thanks

If you would like to try out Vultr, and give me a small tip, you could use my
[Vultr affiliate link](http://www.vultr.com/?ref=6827040) for a new account
with some testing credits.
