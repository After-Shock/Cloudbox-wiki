

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:0 orderedList:1 -->

- [Intro](#intro)
- [URL](#URL)
- [Setup](#setup)
- [API](#api-key)

<!-- /TOC -->

## Intro


[NZBHydra](https://github.com/theotherp/nzbhydra) (by TheOtherP) is a meta search tool for NZB indexers. It provides easy access to a number of NZB indexers. You can search all your indexers from one place and use it as indexer source for tools like Sonarr or CouchPotato.


![](https://i.imgur.com/FZnV0Ru.png)


_Note: By default, Cloudbox will install NZBHydra1. Once NZBHydra2 is out of beta, it will be replaced the current one (you may still install NZBHydra2, if you decide)._ 

> Desimaniac's tips:
> Personally, I add all my indexers in to NZBHydra but I don't connect it with 
> Sonarr or Radarr. Instead, I add all my indexers into Sonarr and Radarr, as 
> well, and use NZBHydra as a separate tool to see what's available online and, if 
> need be, to send it directly to NZBGet.


## URL

- URL to access NZBHydra: https://nzbhydra._yourdomain.com_

## Setup

Enter setup by clicking on "Config" at the top.

1. "Authorization":

    1. Change "Auth type" to `Login form`.

    1. Set all the options below to `ON`.
    1. Click "Add new user". 
    1. Fill in your username and password.
    1. Click "Save" (top right).
    
    ![](https://i.imgur.com/IAxSk4P.png)

 1. Indexers:

    - Add your indexers. Be sure to click "Save" when done.

 1. Downloaders:

    1. "Add new downloader" -> "NZBGet".

    1. Fill in the following:
       - Name: NZBGet
       - Host: `nzbget`
       - Port: `6789`
       - Use SSL: `OFF`
       - Username: [[Your NZBGet Username| First-Time-Install: NZBGet]]
       - Password: [[Your NZBGet Password| First-Time-Install: NZBGet]]
       - Default category: _Leave Blank_ (`No category` doesn't work too well)
       - NZB access type: `Redirect to indexer`
       - NZB adding type: `Upload NZB` (works better than `Send link`) 
  
       ![](https://i.imgur.com/n3ZV0Ki.png)

## API Key

To find the NZBHydra API Key, go to "Config" --> "Main". This will be used later in [[Sonarr|First-Time-Install: Sonarr#nzbhydra]] and [[Radarr|First-Time-Install: Radarr#nzbhydra]].