














1. Sign up for [Cloudflare](https://www.cloudflare.com/).

1. Set your name server on your domain registrar's website (e.g. GoDaddy, Namecheap) to what Cloudflare says.

1. Go to the "Crypto" tab and set SSL to "Full (strict)"

1. Go to the "Overview" tab, click "Get your API key", then retrieve your "Global API Key".

1. Run python script

   ```
   python3 cloudflared.py
   ```

1. Enter your email address, API key, domain, and server IP. 

1. Script will create / update all the subdomains with your server IP and enable proxy for Plex.