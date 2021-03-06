
1. Sign up for a free [Cloudflare](https://www.cloudflare.com/) account.

1. Set the Name Servers to what Cloudflare instructs you to on your Domain Registrar's website (e.g. GoDaddy, Namecheap, etc). _You do not need to make changes to the DNS settings there._

   - Ex. Namecheap.com -> "Dashboard" -> your domain -> "Manage" -> "Name Servers" -> "Custom DNS" -> add the nameservers in.

     ![](https://i.imgur.com/K4OI1XD.png)

1. Go to [Cloudflare.com](https://www.cloudflare.com/). 

   1. Under the "Crypto" tab, set "SSL" to `Full (strict)`.

      ![](https://i.imgur.com/ph1pNZx.png)

   1. Under the "DNS" tab, add the A records for all your [[subdomains | Basics: Accessing Cloudbox Apps#default apps]], with the IP address pointing to your server. Set the `plex` subdomain to `DNS and HTTP proxy (CDN)` (click the cloud icon). The others can be left as `DNS Only`, or  `DNS and HTTP proxy (CDN)` if you wish.

      _Note 1: If you have a separate Plex and Feeder setup, you will need to create A Records for both IP addresses (Plex and Feeder boxes) and set them to their respective subdomains._

      _Note 2: From now on, any DNS settings changes and/or adding of subdomains will now be done on Cloudflare instead of your Domain Registrar's website._



      ![](https://i.imgur.com/YxEFms3.png)
   
