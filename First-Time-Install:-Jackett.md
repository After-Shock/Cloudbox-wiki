Jackett lets you use a bunch of additional torrent providers with programs such as Sonarr and Radarr. You can also use it as a meta search tool to find torrents, yourself. 

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

1. Click "Add Indexer" to add your favorite indexers (i.e. [[torrent trackers| First-Time-Install: Prerequisites#6-preferred-downloading-method]]). 

1. When adding indexers into [[Sonarr|First-Time-Install: Sonarr#jackett]]/[[Radarr|First-Time-Install: Radarr#jackett]], you will need: 

    1. Indexer's Torznab Feed 

         - Copy this by clicking on "Copy Torznab Feed" button next to the Indexer. 

         - You will need to replace...

           - `https` with `http`
           
           - `jackett.yourdomain.com` with `jackett:9117`

    1. Jacket API Key

