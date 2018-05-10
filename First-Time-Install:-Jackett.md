[Jackett](https://github.com/Jackett/Jackett) (based on the original work of Matthew Little aka zone117x) is a web-based app that acts like a proxy server, directing search queries from download clients (eg Sonarr) to torrent tracker sites and sending the results back. Download clients can also use Jackett to fetch RSS feeds from tracker sites. Finally, it can be used as a meta search tool to find torrents, right from within the app.


![](https://i.imgur.com/kgRrhEo.png)

## 1. Accessing Jackett

 - To access Jackett, visit http://jackett._yourdomain.com_

## 2. Settings
  
   ![](https://i.imgur.com/MCbRSr9.png)


### Setting Admin password

Under "Jackett Configuration": 

1. Set "Admin password" to your preferred password.

1. Click "Set Password".

1. Jackett will now refresh and ask you to log in with your admin password.

   ![](https://i.imgur.com/hRJr1Fh.png)

### Disabling Auto Update

Under "Jackett Configuration": 

1. Check "Disable auto update".

1. Check "External access".

1. Click "Apply server settings". 

1. The page will now reload.  




## 3. Adding Indexers to Sonarr/Radarr

Under "Configured Indexers":

1. Click "Add Indexer" to add your favorite indexers (i.e. [[torrent trackers| Basics: Prerequisites#6-preferred-downloading-method]]). 

1. When adding indexers into [[Sonarr|First-Time-Install: Sonarr#jackett]]/[[Radarr|First-Time-Install: Radarr#jackett]], you will need: 

    1. Indexer's Torznab Feed 

         - Copy this by clicking on "Copy Torznab Feed" button next to the Indexer. 

         - You will need to replace...

           - `https` with `http`
           
           - `jackett.yourdomain.com` with `jackett:9117`

    1. Jacket API Key

