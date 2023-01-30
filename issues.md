# Issues

---

## Configuring HTTPS using LetsEncrypt

I was attempting to configure HTTPS using LetsEncrypt, as the manual certs weren't allowing me to access my instance via the mobile app due to security issues with self-signed certs.

I edited the `server_name` in `/etc/nginx/sites-enabled/nginx-passbolt.conf` correctly, ensured the server was reachable by allowing , and verified the DNS A record was pointing at my instances Elastic IP.

However, running `sudo dpkg-reconfigure passbolt-ce-server` and configuring the nginx server using the `auto` option with the following options

* Passbolt domain name: `passbolt.mydomain.com`
* Letsencrypt email: `me@mydomain.com`

resulted in the following error message:

```
Challenge failed for domain passbolt.mydomain.com
http-01 challenge for passbolt.mydomain.com
Cleaning up challenges
Some challenges have failed.

IMPORTANT NOTES:
 - The following errors were reported by the server:

   Domain: passbolt.mydomain.com
   Type:   connection
   Detail: MY_ELASTIC_IP: Fetching
   http://passbolt.mydomain.com/.well-known/acme-challenge/0sU3EggNkd-h_TEcAJSGtCTE6yseLNjnUjq12M5klGw:
   Timeout during connect (likely firewall problem)

   To fix these errors, please make sure that your domain name was
   entered correctly and the DNS A/AAAA record(s) for that domain
   contain(s) the right IP address. Additionally, please check that
   your computer has a publicly routable IP address and that no
   firewalls are preventing the server from communicating with the
   client. If you're using the webroot plugin, you should also verify
   that you are serving files from the webroot path you provided.
```

After finding a community forum post (see Passbolt Forums - LetsEncrypt Issue under [Acknowledgements](README.md##acknowledgements))
I navigated to ` /etc/nginx/sites-enabled/nginx-passbolt.conf` & saw that my configuration showed

```
    listen 443 ssl http2;
    listen [::]:80;
```

My `nginx-passbolt.conf` was missing the line `listen 80;` below `listen [::]:80;` and above the ssl_certificate line.

Re-running `sudo dpkg-reconfigure passbolt-ce-server` generated my LetsEncrypt certificate successfully, and I was able to connect my phone after running `sudo systemctl reload nginx`.

## Importing Passwords

When attempting to import my existing passwords file in to Passbolt, my instance kept hanging for >15 minutes at a time with no noticeable progress.

Multiple reboots later I decided to temporarily upgrade the instance type to a *t2.medium*. After the upgrade, I was able to import my passwords without issue, and switching back to *t2.micro* after the import has given me no issues.