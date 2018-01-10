You can use Cloudflare to setup a CDN with your Plex server. To see if this benefits your case scenario, try it out and compare the results. 

Once Cloudflare is setup, any DNS settings changes and/or adding of subdomains will now be done on Cloudflare instead of your Domain Registrar's website.

_Note: Only set this up once your Cloudbox is up and running; to make sure that domain DNS settings, Nginx-Proxy, SSL certificates are all working ok._

There are two ways to setup this up: 

- [[via Script|Cloudflare via Script]] (recommended) 

- [[Manually|Cloudflare Manually]]