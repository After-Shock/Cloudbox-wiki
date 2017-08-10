## 1. Install Ansible ###

```
sudo apt-get install software-properties-common
sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install ansible
```

Note: press `Y` when asked to confirm.

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