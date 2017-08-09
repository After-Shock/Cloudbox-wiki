# Prerequisites

## 1. Dedicated Server

Get an Ubuntu 16.04 server from a hosting company (eg. Hetzner.de).



## 2. Domain Name
### Paid Domain Name(recommended)
1. Get a domain name from any domain name registry (eg. Namecheap.com, Godaddy.com)
2. Set a wildcard DNS for `*` to your server IP. 
    Example Namecheap: Domain List > Manage > Advanced DNS > Add New Record > A Record > `*` for Host > Server IP for Value.

![](http://i.imgur.com/CjjsRDi.png)

### Free Domain Name
1. Go to http://www.freenom.com, create a free account, and find a domain name to register. 
2. Services > My Domains > Manage Domain > Manage Freenom DNS.
3. Add these A Records, with Target being your server IP.

    ![](http://i.imgur.com/YK5kbso.png)
4. Save Changes.

## Cloud Storage ## 

Cloudbox stores the media unencrypted in Google Drive and utilizes Plexdrive to access it, so if your using Amazon or prefer encryption, look elsewhere. We recommend creating a [G-Suite Business Account](gsuite.google.com/pricing.html).