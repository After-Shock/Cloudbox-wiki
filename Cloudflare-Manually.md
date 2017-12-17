
1. Sign up for a free [Cloudflare](https://www.cloudflare.com/) account.

1. Set the nameservers to what Cloudflare instructs you to on your domain registrar's website (e.g. GoDaddy, Namecheap, etc). _You do not need to make changes to the DNS settings there._

   - Ex. Namecheap.com -> Dashboard -> your domain -> Manage -> Name Servers -> Custom DNS -> add the nameservers in.

     ![](https://i.imgur.com/K4OI1XD.png)

1. Go to [Cloudflare.com](https://www.cloudflare.com/). 

   1. Under the "Crypto" tab, set SSL to "Full (strict)".

     ![](https://i.imgur.com/ph1pNZx.png)

   1. Under the "DNS" tab, add the DNS records for your subdomains, including `*` and `www`, with the IP address pointing to your server. Set Plex subdomain to `DNS and HTTP proxy (CDN)` (click the cloud icon). Leave the others off.

      _Note: If you have a separate Plex and Feeder setup, you will need to set the Plex and Feeder Cloudboxes IP addresses with their respective subdomains._

      ![](https://i.imgur.com/YHbDAcM.png)
   
