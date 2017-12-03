<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:0 orderedList:1 -->

1. [Presumptions](#1-presumptions)
2. [Dedicated Server](#2-dedicated-server)
3. [Domain Name](#3-domain-name)
4. [Google Drive Account](#4-google-drive-account)
5. [Plex Account](#5-plex-account)
6. [Preferred Downloading Method](#6-preferred-downloading-method)

<!-- /TOC -->
---

## 1. Presumptions

Cloudbox assumes you have a basic understanding of Linux, Docker containers, BitTorrent, and Usenet, and are also familiar with Sonarr, Radarr, NZBGet, rTorrent/ruTorrent, and Plex. 

The guides in this wiki are only meant to setup Cloudbox specific settings into the various apps that are installed with Cloudbox (e.g. Sonarr, Radarr, Plex, etc) and are not meant to be a full setup for, or an introduction to, the workings of these apps. 

If you wish to learn more about them, you can easily find a ton of guides for them online (e.g. [HTPC Guides](https://www.htpcguides.com), YouTube, etc). 


## 2. Dedicated Server

Get a server hosting company (e.g. Hetzner) with Ubuntu 16.04 LTS installed. Cloudbox has only been tested to work on on an Intel / AMD64 machines. ARM based servers are not supported.


_Note: If you are using a Scaleway server, read [[this|FAQ#if-you-are-using-a-scaleway-server]]._

## 3. Domain Name

Cloudbox apps will be accessed via https://appname._yourdomain.com_ (see [[Accessing Cloudbox Apps]]). To set this app follow the below instructions.

### i. Paid Domain Name (recommended)
1. Get a domain name from any domain name registry (e.g. Namecheap.com, Godaddy.com, Namesilo.com, etc).
2. Set a wildcard DNS for `*` to your server IP address.

   | **Type** | **Host** | **Value**                | **TTL**   |
   | -------- |:-------- | ------------------------ |:--------- |
   | A Record | *        | _Your server IP address_ | Automatic |

   _Note: Make sure there is also an A Record for the bare domain (e.g. `@` for host)._
    
   Example: For Namecheap.com, go to Domain List > Manage > Advanced DNS > Add New Record > A Record > `*` for Host > Server IP for Value.

   ![](http://i.imgur.com/I7h5jSs.png)

### ii. Free Domain Name (via freenom.com)
1. Visit http://www.freenom.com, create a free account, and find a domain name to register.
2. Go to "Services" > "My Domains" > "Manage Domain" > "Manage Freenom DNS".
3. Add these A Records, with "Target" being your server IP address (wildcard DNS is not allowed at Freenom).

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

## 4. Google Drive Account

Cloudbox stores the media unencrypted in Google Drive and utilizes Plexdrive to access it. So if you want to use another cloud storage provider and/or prefer encryption, Cloudbox may not be for you (see [[FAQ]]). We recommend creating a [G-Suite Business](https://gsuite.google.com/pricing.html) account for larger storage space.

Media will be stored in `Movies` and `TV` folders, all within a `Media` folder in root (i.e. `/Media`).<a href="#note1" id="note1ref"><sup>[1]</sup></a> If you have media in other folders, simply move them into these folders via the [Google Drive website](https://www.google.com/drive/). 


   ```
   Media
   ├── Movies
   └── TV
   ```

Note: All the paths/folders mentioned are **CASE SENSITIVE** (see  [[Paths]]). 


## 5. Plex Account

You'll need a Plex account. 

If you don't already have one, please visit https://www.plex.tv to create a free account.



## 6. Preferred Downloading Method

To use Cloudbox, you will need to choose which method you will use to download your media with. It can either be [Usenet, Torrents, or both](https://www.htpcguides.com/comparing-usenet-vs-torrents/). 

### i. Usenet

If you plan on using [Usenet](https://www.reddit.com/r/usenet/wiki/faq#wiki_usenet_faq) (i.e. Newsgroups) with Cloudbox, you'll need 2 things: a [Usenet provider](https://www.reddit.com/r/usenet/wiki/providers) and a [Usenet indexer](https://www.reddit.com/r/usenet/wiki/indexers). We recommend you have multiple indexers (and even multiple providers) to better your chances at finding and downloading media. 


### ii. BitTorrent

If you plan on using torrents with Cloudbox, we recommend you have access to a [private torrent tracker](https://www.reddit.com/r/trackers/wiki/getting_into_private_trackers) as most servers don't allow public ones. However, if you still want to use public torrent trackers with Cloudbox, you are free to do so. 



---


 <sub> <a id="note1" href="#note1ref"><sup>1</sup></a> If you would like to customize your Plex libraries beyond what is listed above, see [[Customizing Plex Libraries]].</sub>