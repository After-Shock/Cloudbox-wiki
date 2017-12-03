


<!-- TOC depthFrom:1 depthTo:2 withLinks:1 updateOnSave:0 orderedList:0 -->

- [Overview](#overview)
- [Details](#details)


<!-- /TOC -->


# Overview

Cloudox comes with some useful command line tools and scripts. Some are meant to be utilized by Cloudbox, automatically (e.g. fail2ban, torrentcleanup.py, etc), and some are for your usage. 

|  <pre>                   </pre>  Name                 | <pre>              </pre>  Type       | <pre>                                                          </pre> Description                                                                                    |    <pre>                                     </pre> Invoked by                        |  <pre>                                                   </pre> Homepage                                                           |
|:---------------------- |:----------- |:---------------------------------------------------------------------------------------------- |:------------------------------------ |:------------------------------------------------------------------- |
| htop                   | application | Interactive process viewer for Unix.                                                          | `htop`                               | http://hisham.hm/htop/                                              |
| ctop                   | application | Top-like interface for container metrics.                                                      | `ctop`                               | https://ctop.sh/                                                    |
| iotop                  | application | Top like utility for disk I/O.                                                                 | `iotop`                              | http://guichaz.free.fr/iotop/                                       |
| nload                  | application | Monitor network traffic and bandwidth usage in real time.                                      | `nload`                              | http://www.roland-riegel.de/nload/                                  |
| vnstate                | application | Network traffic monitor for that keeps a log of network traffic for the selected interface(s). | `vnstat`                             | http://humdi.net/vnstat/                                            |
| nethogs                | application | Small 'net top' tool that groups bandwidth by process.                                         | `nethogs`                            | https://github.com/raboof/nethogs                                   |
| ngrok                  | application | Secure tunnels to localhost.                                                                   | `ngrok`                              | https://ngrok.com/                                                  |
| ufw                    | application | UFW, or Uncomplicated Firewall, is a front-end to iptables.                                    | `ufw`                                | https://launchpad.net/ufw                                           |
| fail2ban               | application | Ban hosts that cause multiple authentication errors.                                           | `fail2ban`                           | http://www.fail2ban.org                                             |
| speedtest-cli          | application | Command line interface for testing internet bandwidth using speedtest.net                      | `speedtest-cli`                      | https://github.com/sivel/speedtest-cli                              |
| Rclone                 | application | "rsync for cloud storage".                                                                     | `rclone`                             | https://rclone.org/                                                 |
| tree                   | application | Displays an indented directory tree, in color.                                                 | `tree`                               | http://mama.indstate.edu/users/ice/tree/                            |
| ncdu                   | application | Disk usage analyzer with an ncurses interface.                                                 | `ncdu`                               | https://dev.yorhel.nl/ncdu                                          |
| GNU Midnight Commander | application | A visual file manager.                                                                         | `mc`                                 | https://midnight-commander.org/                                     |
| hostess                | application | Tool for tweaking local DNS by managing your /etc/hosts file.                                  | `hostess`                            | https://github.com/cbednarski/hostess                               |
| logrotate              | application | Utility is designed to simplify the administration of log files.                               | `logrotate`                          | https://fedorahosted.org/logrotate/                                 |
| npm                    | application | Package manager for Node.js modules.                                                           | `npm`                                | https://www.npmjs.com/                                              |
| frontail               | application | Node.js application for streaming logs to the browser, like a tail -F with a UI.               | `frontail`                           | https://github.com/mthenw/frontail                                  |
| revoke_certs.sh        | script      | Revoke all of the SSL certifications for your domain                                           | `/opt/scripts/nginx/revoke_certs.sh` | https://github.com/Cloudbox/Cloudbox/wiki/Revoking-SSL-Certificates |
| certbot                | application | Fetches and revokes certificates from Let’s Encrypt. Used by revoke_certs.sh.                  | `certbot`                            | https://certbot.eff.org/                                            |
| TorrentCleanup.py      | script      | Cleans up extracted media files in Rutorrent's downloads folder.                               | Sonarr / Radarr                      | Credit: https://github.com/l3uddz                                   |

# Details
-Work in progress-





TorrentCLeanup.py has been explained in the Sonarr section, but in a nutshell, sonarr/radarr launches this script if you set it up, and it will scan the folder of the file that was imported, if rars exist, delete the file that was imported. this is useful for torrent sites that allow rars, as it will only leave you with the imported file (before its uploaded to google) and just the rars for seeding, instead of also leaving the extracted file. 



( ```cd / && sudo ncdu -x```)

