# Configuration of the bhumi.ngo domain

This documentation describes the changes made to configure Bhumi's website with domain with effect from August 13th, 2020.

## Changelog 13-AUG-2020

New configuration:
- The A name DNS record of `bhumi.ngo` points to IP address of bhumi.ngo's EC2 instance, which is running cPanel and with it, Wordpress.

Old configuration:
- The A name DNS record of `bhumi.ngo` pointed to the Cloudways server that hosted the Wordpress website previously.

#### Testing technique used

1. Create a dummy domain, like `my-domain.com` on a third party DNS provider.
2. Create a Cloudflare account and register dummy domain there. Cloudflare will instruct you to change your nameservers to Cloudflare's nameserver as described [here](https://support.cloudflare.com/hc/en-us/articles/205195708-Changing-your-domain-nameservers-to-Cloudflare) 
3. Point nameservers of dummy domain to Cloudflare and wait until the registrar informs you that the nameserver update has been made.
4. Check the `Overview` tab in Cloudflare. If it looks like the one below, you are good to go.
![Successful Nameserver Configuration](docs/domain-config/overview.png)
5. Go to the `DNS` tab and create A name records for `@` (which is root, i.e., `my-domain.com`) and `www` (this depends on whether you want to change the IP to which `www.my-domain.com` points as well). The IP address field should be filled with the new IP. Once that is complete, the configuration of your dummy domain should look like:
![DNS Records Configuration](docs/domain-config/dns-records.png)
6. Click on the `SSL/TLS` tab and make sure that the `Full` configuration is selected, as shown:
![SSL/TLS Configuration](docs/domain-config/ssl-tls.png)
7. Open a new browser tab and go to the address `https://my-domain.com` as well as `https://www.my-domain.com`. Your webpage should now be redirected.
8. If you have been trying multiple times, and it doesn't work, purge Cloudflare's cache by clicking `Purge Cache` in the `Overview` tab as shown below:
![Purge Cache](docs/domain-config/purge-cache.png)

#### `bhumi.ngo` website
For the original website, follow steps 5 through 8 above and replace `my-domain.com` with `bhumi.ngo`.

