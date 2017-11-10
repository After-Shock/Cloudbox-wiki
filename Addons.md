There are afew useful addons/scripts installed by cloudbox that can be utilized by yourself or sonarr/radarr. These are things such as TorrentCleanup.py and revoke_certs.sh (all of which can be found at /opt/scripts in their respective folders).

revoke_certs.sh does as it says, it will iterate your cert folder (/opt/nginx-proxy) and revoke all of the SSL certifications. 

TorrentCLeanup.py has been explained in the Sonarr section, but in a nutshell, sonarr/radarr launches this script if you set it up, and it will scan the folder of the file that was imported, if rars exist, delete the file that was imported. this is useful for torrent sites that allow rars, as it will only leave you with the imported file (before its uploaded to google) and just the rars for seeding, instead of also leaving the extracted file. 

Useful tools installed:

fail2ban is installed which its default configuration is setup to ban after X many failed login attempts.

htop is installed to monitor system metrics (ram/cpu/process usage etc).

ctop is installed to monitor container metrics.

iotop is installed to monitor your disk metrics

nload is installed to monitor current network interface traffic.

vnstat is installed to keep a record of your bandwidth usage.

ufw is installed for easy iptable management.

logrotate is installed (should be by default) to ensure you dont drown in logs.

tree is installed to visualize directories and files.

speedtest-cli is installed to perform quick speedtests (not always accurate)

certbot is also installed, as its required by the revoke_certs script.

ncdu will show you your drive usage (e.g. ```cd / && sudo ncdu -x```)

hostess can be used host modification via cli

ngrok - secure introspectable tunnels to localhost webhook development tool and debugging tool.

nethogs - view traffic stats for individual processes