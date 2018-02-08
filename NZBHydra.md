

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:0 orderedList:0 -->

1. [Accessing NZBHydra](#1-accessing-nzb-hydra)
2. [Setup](#2-setup)
3. [API](#3-api-key)

<!-- /TOC -->


NZBHydra is a meta search for NZB indexers. It provides easy access to a number of raw and newznab based indexers. You can search all your indexers from one place and use it as indexer source for tools like Sonarr or CouchPotato.

By default, Cloudbox will install NZBHydra1. Once NZBHydra2 is out of beta, it will be replaced the current one (you may test out NZBHydra2 later if you decide). 

## 1. Accessing NZBHydra

- To access NZBHydra, visit https://nzbhydra._yourdomain.com_

## 2. Setup

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
       - Username: [[Your NZBGet Username|NZBGet]]
       - Password: [[Your NZBGet Password|NZBGet]]
       - Default category: _Leave Blank_ (`No category` doesn't work too well)
       - NZB access type: `Redirect to indexer`
       - NZB adding type: `Upload NZB` (works better than `Send link`) 
  
       ![](https://i.imgur.com/n3ZV0Ki.png)

## 3. API Key

To find the NZBHydra API Key, go to "Config" --> "Main". This will be used later in [[Sonarr|Sonarr#nzb-hydra]] and [[Radarr|Radarr#nzb-hydra]].