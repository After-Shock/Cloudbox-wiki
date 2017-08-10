## 1. Install Ansible ###

Run the following command. Press `Y` when asked to confirm. 
```
sudo apt-get install python-pip && sudo pip install ansible==2.3.1.0
```
Note: Ansible v2.3.1.0 is the current stable version (v2.3.2.0 has a bug where docker_container state=stopped causes container to be removed).


## 2. Run Cloudbox

1. Go into cloudbox folder

  ```bash
  cd cloudbox
  ```

2. Decide on what type of Cloudbox you want: `full`,`feeder`, or `plex` .

3. Run the following command, with the preferred option from #2 (`--tag "option"`). Quotes are not required.

    Example of a full install:
    ```bash
    sudo ansible-playbook cloudbox.yml --tag full
    ```
4. When asked for a 

sudo ansible-playbook cloudbox.yml --tags full



to continue plex installatio...
https://plex.tv/claim

...

sudo reboot