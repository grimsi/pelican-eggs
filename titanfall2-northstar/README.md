# Titanfall 2 (Northstar)

## Game files mounting
The server does **not** contain the base game files, but they are necessary to use the server.

While the server itself is open-source, the game files are copyrighted and you will need to own a legitimate copy of the game (Titanfall 2)
in order to provide the game files to the server.

More information here: https://r2northstar.gitbook.io/r2northstar-wiki/hosting-a-server-with-northstar/dedicated-server/hosting-on-linux#prepare-titanfall2-server-files

### Correctly mounting the game files
In order to give the server access to the needed game files you will need to create a new mount.

Let's say you copied the game files to your node into the directory `/home/pterodactyl/serverfiles/titanfall2` (you can choose any directory you want of course).  

First of all add the directory of the mount to the config.yml (in `/etc/pterodactyl`) of your node.
```
allowed_mounts:
- /home/pterodactyl/serverfiles
```
After you've done this, restart wings with `systemctl restart wings`.

Now you simply create a mount in the Pterodactyl Panel with the following settings:
1. Set the source to `/home/pterodactyl/serverfiles/titanfall2`
2. Set the target to `/mnt/titanfall2`
3. Set read-only to "true" ("false" will also work, but then you risk that one instance overwrites files for all other instances)
4. For the rest of the settings you can decide what works best for you
5. Create the mount
6. Add the correct node to the list of nodes for the mount
7. Add the Titanfall 2 egg to the list of eggs for the mount

### Correctly configuring the servers
While creating a server with this egg in the panel make sure to select the mount with the server files you created.


**Congratulations!** Your server should be able to find the game files and start.

## Default Server Ports
The default is 37015, if you change it make sure to also change the "Server port" variable.

| Port    | default |
|---------|---------|
| Game    | 37015   |

#### Mods may require ports to be added to the server.
