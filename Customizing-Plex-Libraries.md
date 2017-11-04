In the default Cloudbox install, there only two main Plex libraries: one for Movies and one for TV Shows. With the idea that all movies are to be placed within the `/Media/Movies` folder.

   ```
   Media
   ├── Movies
   └── TV
   ```

If you would like to have custom libraries in Plex, you may do so with this guide. But regardless of what scenario below you choose, the content will always be located within `/Media` folder in your Google Drive (or `/mnt/unionfs/Media` on your server). 



## Scenario 1

You want to place your libraries within the `/Media/Movies` folder.

```
Media
├── Movies
│   ├── 3D
│   ├── 4K
│   ├── Foreign
│   ├── Hollywood
│   └── Kids
└── TV

```


_Note: You could do the same to TV shows (i.e. have multiple sub-dirs within `TV`), but this guide will not go over that. However, the steps are similar to the ones below._

_Note 2: If you have a separate Plex and Feeder setup, the following steps will be done on the server where Plex is installed._


### 1. Create folders in Google Drive


Let's say you wanted to have separate movie libraries for: 3D, 4K, Foreign, Hollywood, and Kids. You would first have to create these folders within the `/Media/Movies` path in Google Drive. `/Media/Movies` folder will contain nothing but these folders.

In our example, we will create the following folders: `/Media/Movies/3D`, `/Media/Movies/4K`, `/Media/Movies/Foreign`, `/Media/Movies/Hollywood`, and `/Media/Movies/Kids`.

### 2. Add Libraries to Plex

You will add each of these folders as separate libraries within Plex (see [[example|Plex#adding-the-movie-library]]). You may name these libraries as whatever you want. The folders will be located in the `/data/Movies` folder.

In our example, this will be: `/data/Movies/3D`, `/data/Movies/4K`, `/data/Movies/Foreign`, `/data/Movies/Hollywood`, and `/data/Movies/Kids`.

### 3. Retrieve Plex Library Section IDs

1. On the server's shell, run the following command:

    ```
    /opt/plex_autoscan/scan.py sections
    ```

1. Your screen will now show something similar to this:

    ```
    1: 3D
    2: 4K
    3: Foreign
    4: Hollywood
    5: Kids
    6: TV
    ```

1. The list here shows your section IDs in the format of `SECTION ID: LIBRARY NAME`. Note: Your section IDs may be different as it is based on the order you added them in Plex.



### 4. Modify Plex Autoscan Config

1. On the server's shell, run the following command:

    ```
    nano /opt/plex_autoscan/config/config.json
    ```

1. Scroll down to the `PLEX_SECTION_PATH_MAPPINGS` section.

1. Under this section, you will need to add your section IDs and the library paths (as located within the `/Media` folder in Google Drive). The format is `"SECTION_NUMBER": ["path"]`.

   Make sure the path is within quotes (`"/Movies/3D"`) and there is a comma (`,`) after the close bracket (`]`) - all except the last one (see example below).

1. After the changes, the section will now look similar to this:

   ```json
   "PLEX_SECTION_PATH_MAPPINGS": {
      "1": [
          "/Movies/3D/"
      ],
      "2": [
          "/Movies/4K/"
      ],
      "3": [
          "/Movies/Foreign/"
      ],
      "4": [
          "/Movies/Hollywood/"
      ],
      "5": [
          "/Movies/Kids/"
      ],
      "6": [
          "/TV/"
      ]
   },
   ```

1. `Ctrl-x`, `y`, and `enter` to save.


1. Restart Plex Autoscan: `sudo systemctl restart plex_autoscan`


### 5. Modify UnionFS Cleaner Config

1. On the server's shell, run the following command:

    ```
    nano /opt/unionfs_cleaner/config.json
    ```

1. Scroll down to the `rclone_remove_empty_on_upload` section.

1. Change `"/mnt/local/Media/Movies": 1` to `"/mnt/local/Media/Movies": 2`. 

   1. This will tell UnionFS Cleaner to not delete the folders immediately under `/mnt/local/Media/Movies` during cleanup.  

   1. Make sure there is a comma (`,`) at the end of all `"path": #` lines - all except the last one (see example below).

1. After the changes, the section will now look similar to this:

   ```json
   "rclone_remove_empty_on_upload": {
       "/mnt/local/Media/Movies": 2,
       "/mnt/local/Media/TV": 1
   },
   ```

1. `Ctrl-x`, `y`, and `enter` to save.

1. UnionFS Cleaner will restart itself when it detects config.json has changed.


### 6. Change root paths in Radarr

Set your Movie Paths in Radarr to reflect the new sub-dirs (e.g. `/movies/3D`), see the wiki on [[Radarr|Radarr#8-adding-the-movies-path]].

## Scenario 2 (less preferred)

You want to place your libraries within the `/Media` folder.

```
Media
├── Movies-3D
├── Movies-4K
├── Movies-Foreign
├── Movies-Hollywood
├── Movies-Kids
└── TV

```




_Note: You could do the same to TV shows, but this guide will not go over that. However, the steps are similar to the ones below._

_Note 2: If you have a separate Plex and Feeder setup, the following steps will be done on the server where Plex is installed._


### 1. Create folders in Google Drive


Let's say you wanted to have separate movies libraries for: general movies folder, 3D, 4K, Foreign, Hollywood, and Kids. You would first have to create these folders within the `/Media` path in Google Drive. `/Media/` folder will contain nothing but these folders (and the `TV` folder).

In our example, we will create the following folders: `/Media/Movies-3D`, `/Media/Movies-4K`, `/Media/Movies-Foreign`, `/Media/Movies-Hollywood`, and `/Media/Movies-Kids`.

### 2. Add Libraries to Plex

You will add each of these folders as separate libraries within Plex (see [[example|Plex#adding-the-movie-library]]). You may name these libraries as whatever you want. The folders will be located in the `/data` folder.

In our example, this will be: `/data/Movies-3D`, `/data/Movies-4K`, `/data/Movies-Foreign`, `/data/Movies-Hollywood`, and `/data/Movies-Kids`.


### 3. Retrieve Plex Library Section IDs

1. On the server's shell, run the following command:

    ```
    /opt/plex_autoscan/scan.py sections
    ```

1. Your screen will now show something similar to this:

    ```
    1: 3D
    2: 4K
    3: Foreign
    4: Hollywood
    5: Kids
    6: TV
    ```

1. The list here shows your section IDs in the format of `SECTION ID: LIBRARY NAME`. Note: Your section IDs may be different as it is based on the order you added them in Plex.


### 4. Modify Plex Autoscan Config

1. On the server's shell, run the following command:

    ```
    nano /opt/plex_autoscan/config/config.json
    ```

1. Scroll down to the `PLEX_SECTION_PATH_MAPPINGS` section.

1. Under this section, you will need to add your section IDs and the library paths (as located within the `/Media` folder in Google Drive). The format is `"SECTION_NUMBER": ["path"]`.

   Make sure the path is within quotes (`"/Movies-3D"`) and there is a comma (`,`) after the close bracket (`]`) - all except the last one (see example below).

1. After the changes, the section will now look similar to this:

   ```json
   "PLEX_SECTION_PATH_MAPPINGS": {
      "1": [
          "/Movies-3D/"
      ],
      "2": [
          "/Movies-4K/"
      ],
      "3": [
          "/Movies-Foreign/"
      ],
      "4": [
          "/Movies-Hollywood/"
      ],
      "5": [
          "/Movies-Kids/"
      ],
      "6": [
          "/TV/"
      ]
   },
   ```

1. `Ctrl-x`, `y`, and `enter` to save.


1. Restart Plex Autoscan: `sudo systemctl restart plex_autoscan`


### 5. Modify UnionFS Cleaner Config

1. On the server's shell, run the following command:

    ```
    nano /opt/unionfs_cleaner/config.json
    ```

1. Scroll down to the `rclone_remove_empty_on_upload` section.

1. Add your paths under paths under it. (e.g. `"/mnt/local/Media/Movies-3D": 1`)

   1. This will tell UnionFS Cleaner to not delete the folders immediately under `/mnt/local/Media/Movies` during cleanup.  

   1. Make sure there is a comma (`,`) at the end of all `"path": #` lines - all except the last one (see example below).

1. After the changes, the section will now look similar to this:

   ```json
   "rclone_remove_empty_on_upload": {
       "/mnt/local/Media/Movies-3D": 1,
       "/mnt/local/Media/Movies-4K": 1,
       "/mnt/local/Media/Movies-Foreign": 1,
       "/mnt/local/Media/Movies-Hollywood": 1,
       "/mnt/local/Media/Movies-Kids": 1,
       "/mnt/local/Media/TV": 1
   },
   ```

1. `Ctrl-x`, `y`, and `enter` to save.

1. UnionFS Cleaner will restart itself when it detects config.json has changed.


### 6. Change root paths in Radarr

Set your Movie Paths in Radarr to reflect the new sub-dirs (e.g. `/mnt/unionfs/Media/Movies-3D`), see the wiki on [[Radarr|Radarr#8-adding-the-movies-path]].