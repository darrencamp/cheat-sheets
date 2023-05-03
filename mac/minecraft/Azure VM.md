---
tags:
  - azure
---
Minecraft Notes
===============


1. Service control ie systemctl init files are in /etc/systemd/system
2. Minecraft itself is stored in /srv

building craftbukkit and spigot
-------------------------------
https://www.spigotmc.org/wiki/buildtools

1. go to build directory and create a new directory for the version
2. download BuildTools.jar to that directory, curl https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar -o BuildTools.jar
3. follow the steps from the link above
3.1 to get a build of craftbukkit use these params on buildtools --compile craftbukkit --rev <require version>
4. backup the current server, tar -cpvzf ~/backup/x-minecraft-server-{datetime}.tar.gz /srv/x_minecraft_server
5. copy in new minecraft, spiggot and craftbukkit to minecraft server directory
6. update x-minecraft-server.service in /etc/systemd/system

Service control notes:
----------------------
to start experimental service:
sudo systemctl start x-minecraft-server

status: sudo systemctl status x-minecraft-server

there is also 1.11.2 vanilla minecraft service

Links:
https://minecraft.net/en/download/server


1.16.3 - harrycraft
1.11.2 - harryworld
1.11.2 - harryworld_x
1.11.2 - harryworld_x_old
1.16.3 - harryworld_x

harrycraft.20221230.backup
-rw-rw-r--  1 admin.minecraft admin.minecraft 243497817 Dec 30 05:44 harryworld.20221230.backup
-rw-rw-r--  1 admin.minecraft admin.minecraft 258456763 Dec 30 05:47 harryworld_x_1.11.2.20221230.backup
-rw-rw-r--  1 admin.minecraft admin.minecraft 337312123 Dec 30 05:46 harryworld_x.20221230.backup
-rw-rw-r--  1 admin.minecraft admin.minecraft 252993683 Dec 30 05:48 harryworld_x_old_1.11.2.20221230.backup



secure copy scp
scp <source> <destination> eg scp user@host:path local-path

