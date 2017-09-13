## 1. Dedicated Server

Get an Ubuntu 16.04 server from a hosting company (eg. Hetzner.de). This has been tested on an AMD64 / INTEL64 machine. ARM based servers (e.g. Digital Ocean, Scaleway) are not supported.



## 2. Domain Name

Cloudbox apps will be accessed via https://appname._yourdomain.com_ (see [[Accessing Cloudbox Apps]]). To set this app follow the below instructions.

### i. Paid Domain Name (recommended)
1. Get a domain name from any domain name registry (eg. Namecheap.com, Godaddy.com)
2. Set a wildcard DNS for `*` to your server IP.
    
    |   **Type**   | **Host** | **Value**                   |     **TTL** |
    | ------------ | :--------: | ------------------------- | :-----------: |
    | A Record       | *        | _your server ip address_  |  Automatic  |

    Example: For Namecheap.com, go to Domain List > Manage > Advanced DNS > Add New Record > A Record > `*` for Host > Server IP for Value.

   ![](http://i.imgur.com/I7h5jSs.png)

### ii. Free Domain Name
1. Visit http://www.freenom.com, create a free account, and find a domain name to register.
2. Go to "Services" > "My Domains" > "Manage Domain" > "Manage Freenom DNS".
3. Add these A Records, with Target being your server IP (wildcard DNS not allowed).

    |   **Name**   | **Type** | **TTL** |        **Target**        |
    | ------------ | -------- | ------- | ------------------------ |
    | jackett      | A        | 14440   | _your server ip address_ |
    | nzbget       | A        | 14440   | _your server ip address_ |
    | nzbhydra     | A        | 14440   | _your server ip address_ |
    | organizr     | A        | 14440   | _your server ip address_ |
    | plex         | A        | 14440   | _your server ip address_ |
    | plexpy       | A        | 14440   | _your server ip address_ |
    | plexrequests | A        | 14440   | _your server ip address_ |
    | portainer    | A        | 14440   | _your server ip address_ |
    | radarr       | A        | 14440   | _your server ip address_ |
    | rutorrent    | A        | 14440   | _your server ip address_ |
    | sonarr       | A        | 14440   | _your server ip address_ |




4. Save Changes.

## 3. Google Drive account ##

* Cloudbox stores the media unencrypted in Google Drive and utilizes Plexdrive to access it, so if your using Amazon or prefer encryption, look elsewhere. We recommend creating a [G-Suite Business](gsuite.google.com/pricing.html) account for larger storage space.

* Media will be stored in `Media` folder in root, and `Movies` and `TV` folders within that. If you have media in other folders, simply move them into these folders via the Google Drive web app.<a href="#note1" id="note1ref"><sup>1</sup></a>

    ![](http://i.imgur.com/cRIo3lQ.png)

    <a id="note1" href="#note1ref"><sup>1</sup></a> Although these folders are not meant to be changed, you can still separate content into multiple libraries by creating subfolders within the Movies and TV folders, see [[Customizing Plex Libraries]].

## 4. Plex.tv account

* You'll need a Plex account (it's free). If you don't already have one, please visit http://www.plex.tv and create one.
