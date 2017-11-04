
1. Sign up for CloudFlare

1. Move the nameservers of your domain (domain registrar's website) over to the ones provided during CloudFlare’s setup.

1. Under the "Crypto" tab, set SSL to Full (Strict)

   ![](https://i.imgur.com/ph1pNZx.png)

1. Add the DNS records for your subdomains, including `*` and `www`. Set Plex subdomain to `DNS and HTTP proxy (CDN)` (click the cloud icon). Leave the others off.

   ![](https://i.imgur.com/YHbDAcM.png)
   
1. That's it. 
