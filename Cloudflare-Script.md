Script will create / update all the subdomains with your server IP address and enable proxy for Plex.

1. Sign up for [Cloudflare](https://www.cloudflare.com/).

1. Set your name server on your domain registrar's website (e.g. GoDaddy, Namecheap) to what Cloudflare says.

1. Go to the "Crypto" tab and set SSL to "Full (strict)"

1. Go to the "Overview" tab, click "Get your API key", then retrieve your "Global API Key".

1. Run the following python script:

   ```
   python3 /opt/scripts/cloudflare/cloudflared.py
   ```

1. When asked, enter your email address, API key, domain, and server IP address.