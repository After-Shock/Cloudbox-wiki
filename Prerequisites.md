# Prerequisites

## 1. Dedicated Server

Get an Ubuntu 16.04 server from a hosting company (eg. Hetzner.de).



## 2. Domain Name
### i. Paid Domain Name (recommended)
1. Get a domain name from any domain name registry (eg. Namecheap.com, Godaddy.com)
2. Set a wildcard DNS for `*` to your server IP. 
    Example Namecheap: Domain List > Manage > Advanced DNS > Add New Record > A Record > `*` for Host > Server IP for Value.

![](http://i.imgur.com/I7h5jSs.png)

### ii. Free Domain Name
1. Go to http://www.freenom.com, create a free account, and find a domain name to register. 
2. Services > My Domains > Manage Domain > Manage Freenom DNS.
3. Add these A Records, with Target being your server IP (wildcard DNS not allowed).

    ![](http://i.imgur.com/wsK9UFU.png)
4. Save Changes.

## 3. Cloud Storage ## 

* Cloudbox stores the media unencrypted in Google Drive and utilizes Plexdrive to access it, so if your using Amazon or prefer encryption, look elsewhere. We recommend creating a [G-Suite Business](gsuite.google.com/pricing.html) account.

* Media will be stored in `Media` folder in root, and `Movies` and `TV` folders within that. If you have media in other folders, simply move them into these folders via the Google Drive web app.<a href="#note1" id="note1ref"><sup>1</sup></a>

    ![](http://i.imgur.com/cRIo3lQ.png)

    <a id="note1" href="#note1ref"><sup>1</sup></a> Although these folders are not meant to be changed, you may have other subfolders within Movies and TV, but will require further editing of settings <link to unionfs_cleaner and plex_autoscan configs editing page>.