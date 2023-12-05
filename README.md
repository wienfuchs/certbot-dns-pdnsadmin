[![Build Status](https://travis-ci.com/pan-net-security/certbot-dns-pdnsadmin.svg?branch=master)](https://travis-ci.com/pan-net-security/certbot-dns-pdnsadmin)
[![Coverage Status](https://coveralls.io/repos/github/pan-net-security/certbot-dns-powerdns/badge.svg?branch=master)](https://coveralls.io/github/pan-net-security/certbot-dns-powerdns?branch=master)
![Libraries.io dependency status for latest release](https://img.shields.io/librariesio/release/github/pan-net-security/certbot-dns-powerdns.svg)
![PyPI - Status](https://img.shields.io/pypi/status/certbot-dns-powerdns.svg)

![PyPI - Python Version](https://img.shields.io/pypi/pyversions/certbot-dns-powerdns.svg)


certbot-dns-powerdns
============

PowerDNS DNS Authenticator plugin for [Certbot](https://certbot.eff.org/).

This plugin is built from the ground up and follows the development style and life-cycle
of other `certbot-dns-*` plugins found in the
[Official Certbot Repository](https://github.com/certbot/certbot).

Installation
------------

```
pip install --upgrade certbot
pip install git+https://github.com/wienfuchs/certbot-dns-pdnsadmin@py3+pdns-admin
```

Verify:

```
$ certbot plugins --text

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
* dns-powerdns
Description: Obtain certificates using a DNS TXT record (if you are using
PowerDNS for DNS.)
Interfaces: IAuthenticator, IPlugin
Entry point: dns-powerdns = certbot_dns_powerdns.dns_powerdns:Authenticator
...
...
```

Configuration
-------------

The credentials file e.g. `~/pdns-credentials.ini` should look like this:

```
dns_powerdns_api_url = https://api.your.powerdns-admin.example.org
dns_powerdns_api_key = Your.Secret.PowerDNS-Admin.API.key
```

Usage
-----


```
certbot ... \
        --authenticator dns-powerdns  \
        --dns-powerdns-credentials ~/pdns-credentials.ini \
        certonly
```

FAQ
-----

##### Why such long name for a plugin?

This follows the upstream nomenclature: `certbot-dns-<dns-provider>`.

##### Why do I have to use `:` separator in the name? And why are the configuration file parameters so weird?

This is a limitation of the Certbot interface towards _third-party_ plugins.

For details read the discussions:

- https://github.com/certbot/certbot/issues/6504#issuecomment-473462138
- https://github.com/certbot/certbot/issues/6040
- https://github.com/certbot/certbot/issues/4351
- https://github.com/certbot/certbot/pull/6372

Development
-----------

Create a virtualenv, install the plugin (`editable` mode),
spawn the environment and run the test:

```
virtualenv -p python3 .venv
. .venv/bin/activate
pip install -e .
docker-compose up -d
./test/run_certonly.sh test/pdns-credentials.ini
```

License
--------

Copyright (c) 2019 [DT Pan-Net s.r.o](https://github.com/pan-net-security)
Updates Copyright (c) 2023 [Wienfuchs](https://github.com/wienfuchs)
Original release by [DT Pan-Net s.r.o](https://github.com/pan-net-security) was covered by {APACHE License 2.0](https://www.apache.org/licenses/LICENSE-2.0) as per source code
