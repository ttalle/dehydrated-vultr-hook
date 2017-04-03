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
#!/usr/bin/env bash

APIKEY="XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
```

## Usage

This script can be used in two ways:

### Stand-alone

Set this script as your HOOK script in Dehydrated.

### Using (dehydrated-dispatch-hook)[https://github.com/ttalle/dehydrated-dispatch-hook]

Since the Vultr DNS service only allows for verification it only acts on the
```deploy_challenge``` and ```clean_challenge``` hooks. To deploy your 
certificates you will need another script that does that.

With the dehydrated-dispatch-hook you can combine two hook scripts and
allow another hook to do the deploy actions.

A nice example would be the (dehydrated-vault-hook)[https://github.com/ttalle/dehydrated-vault-hook] script that stores
the certificate, chain and key as a secret in Vault. This enables services
to safely retreive their certificates themselves.
