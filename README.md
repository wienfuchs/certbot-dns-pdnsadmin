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

##### Are you (WienFuchs) affiliated with Pan-Net?

I am not affiliated in any way, I found this nice plugin beeing useful and simply decided to deveolp it a little further, as it did not work for me any longer.

##### Will you (WienFuchs) ensure further updates if needed?

As long as I personally use it (which is expected to be a long period), I will do my best to keep it aup to date and working with recent Python, PowerDNS (-Admin) and Certbot versions. Feel free to place any issues, if needed.


License
--------

Copyright (c) 2019 [DT Pan-Net s.r.o](https://github.com/pan-net-security)

Updates Copyright (c) 2023 [Wienfuchs](https://github.com/wienfuchs)

Original release by [DT Pan-Net s.r.o](https://github.com/pan-net-security) was covered by {APACHE License 2.0](https://www.apache.org/licenses/LICENSE-2.0) as per source code
