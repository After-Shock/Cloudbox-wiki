Script will: (1) add (or update) all the Cloudbox [[sub-domains|Accessing-Cloudbox-Apps]] into Cloudflare, and (2) will enable DNS and HTTP proxy (CDN) for Plex.

Steps to setup Cloudflare are as follows:

1. Sign up for [Cloudflare](https://www.cloudflare.com/).

1. Set the nameservers to what Cloudflare instructs you to on your domain registrar's website (e.g. GoDaddy, Namecheap, etc).

1. Go to the "Crypto" tab and set SSL to "Full (strict)"

1. Go to the "Overview" tab, click "Get your API key", then retrieve your "Global API Key".

1. Run the following python script:

   ```
   python3 /opt/scripts/cloudflare/cloudflared.py
   ```

1. When asked, enter your email address, API key, domain, and server IP address.