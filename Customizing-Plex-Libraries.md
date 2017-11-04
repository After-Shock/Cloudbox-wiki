In the default Cloudbox install, you have two Plex libraries: one for Movies and one for TV Shows (see below).

   ```
   Media
   ├── Movies
   └── TV
   ```

If you would like to have custom libraries in Plex, you may do so with this guide. But regardless of what scenario below you choose, the content will always be within `/Media` folder in your Google Drive. 



## Scenario 1

You want to place your libraries within the `/Media/Movies` folder.

```
Media
├── Movies
│   ├── 3D
│   ├── 4K
│   ├── Foreign
│   └── Hollywood
└── TV

```


_Note: You could do the same to TV shows (i.e. have multiple sub-dirs within `TV`), but this guide will not go over that. However, the steps are similar to the ones below._

_Note 2: If you have a separate Plex and Feeder setup, the following steps will be done on the server where Plex is installed._


### 1. Create folders in Google Drive


Let's say you wanted to have separate movie libraries for: 3D, 4K, Foreign, Hollywood, and Kids. You would first have to create these folders within the `/Media/Movies` path in Google Drive. `/Media/Movies` folder will contain nothing but these folders.

In our example, we will create the following folders: `/Media/Movies/3D`, `/Media/Movies/4k`, `/Media/Movies/Hollywood`, `/Media/Movies/Kids`, and `/Media/Movies/Foreign`.

### 2. Adding Libraries to Plex

You will add each of these folders as separate libraries within Plex (see [[example|Plex#adding-the-movie-library]]). You may name these libraries as whatever you want. The folders will be located in the `/data/Movies` folder.

In our example, this will be: `/data/Movies/3D`, `/data/Movies/4K`, `/data/Movies/Foreign`, `/data/Movies/Hollywood`, and `/data/Movies/Kids`.

### 3. Retrieving Plex Library Section IDs

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



### 4. Modifying Plex Autoscan Config

1. On the server's shell, run the following command:

    ```
    nano /opt/plex_autoscan/config/config.json
    ```

1. Scroll down to the `PLEX_SECTION_PATH_MAPPINGS` section.

1. Under this section, you will need to add your section IDs and the library paths (as located in /Media folder in Google Drive). The format is `"SECTION_NUMBER": ["path"]`.

   Make sure the path is within quotes (`"/Movies/Kids"`) and there is a comma (`,`) after the close bracket (`]`) - all except the last one (see example below).

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


### 5. Modifying UnionFS Cleaner Config

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



## Scenario 2 (WORK IN PROGRESS)

You want to place your libraries within the `/Media` folder.

```
Media
├── Movies
├── Movies-3D
├── Movies-4K
├── Movies-Hollywood
├── Movies-Kids
├── Movies-Foreign
└── TV

```




_Note: You could do the same to TV shows, but this guide will not go over that. However, the steps are similar to the ones below._

_Note 2: If you have a separate Plex and Feeder setup, the following steps will be done on the server where Plex is installed._


### 1. Create folders in Google Drive


Let's say you wanted to have separate movies libraries for: general movies folder, 3D, 4K, Foreign, Hollywood, and Kids. You would first have to create these folders within the `/Media` path in Google Drive. `/Media/` folder will contain nothing but these folders (and the `TV` folder).

In our example, we will create the following folders: `/Media/Movies-3D`, `/Media/Movies-4K`, `/Media/Movies-Hollywood`, `/Media/Movies/Kids`, and `/Media/Movies/Foreign`.

### 2. Adding Libraries to Plex

You will add each of these folders as separate libraries within Plex (see [[example|Plex#adding-the-movie-library]]). You may name these libraries as whatever you want. The folders will be located in the `/mnt/unionfs/Media/` folder.

In our example, this will be: `/data/Movies/3D`, `/data/Movies/4K`, `/data/Movies/Foreign`, `/data/Movies/Hollywood`, and `/data/Movies/Kids`.

### 3. Retrieving Plex Library Section IDs

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



### 4. Modifying Plex Autoscan Config

1. On the server's shell, run the following command:

    ```
    nano /opt/plex_autoscan/config/config.json
    ```

1. Scroll down to the `PLEX_SECTION_PATH_MAPPINGS` section.

1. Under this section, you will need to add your section IDs and the library paths (as located in /Media folder in Google Drive). The format is `"SECTION_NUMBER": ["path"]`.

   Make sure the path is within quotes (`"/Movies/Kids"`) and there is a comma (`,`) after the close bracket (`]`) - all except the last one (see example below).

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


### 5. Modifying UnionFS Cleaner Config

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
