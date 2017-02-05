Multicraft
==========

Open Source Multicraft Scripts All scripts published in this repository are released under the GNU License.

    Copyright (C) 2013  Jonathan Mainguy jon@soh.re

    These scripts are free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.


__Note:__ Zip and .tar.gz files can be downloaded from the [Soh.re Pulp Repo] server.

## Prerequisites
* [Multicraft]

## Installation
__Note:__ Throughout this process we will assume that the defualt installation options for Multicraft were used and that Multicraft was installed at `/home/minecraft/multicraft`, if this is not the case subtitiute this for the correct path.

__Note:__ Throughout this process we will also assume that Multicraft is in multiuser mode.

### __For [Ubuntu]__

#### 1. Installing required packages
Start off by installing `steamcmd` and `git` on your system, do this by typing these commands:
  1. `apt-get update`
  2. `apt-get install steamcmd git zip unzip`
  
#### 2. Cloning this repository
Once you've done that you will need to clone this repository by running:
  1. `cd ~`
  2. `git clone https://github.com/Standouthost/Multicraft.git`
  
#### 3. Moving files and setting file permissions
After that, you will be required to move some files into place:
  1. `~/Multicraft/bin/prepare.sh` needs to be copied into Multicrafts bin directory, you can do this by running `cp ~/Multicraft/bin/prepare.sh /home/minecraft/multicraft/bin/prepare.sh`.
  2. Ensure prepare.sh has the correct owner and file permissions by running `chown root:root /home/minecraft/multicraft/bin/prepare.sh` (This sets the file owner to root) and `chmod 700 /home/minecraft/multicraft/bin/prepare.sh` (This gives Read, Write and Execute permissions only to the files owner).
  3. All Multicraft conf files and run scripts also need to be copied into Multicrafts jar directory (If you wish you can also only copy the ones you wish to use, e.g. if you wish to run an Ark server copy `ark.jar.conf` and `ark.sh` into Multicrafts jar directory), the easiest way to do this is by running `cp -r ~/Multicraft/jar/* /home/minecraft/multicraft/jar/`, this moves all files from `~/Multicraft/jar/` into Multicrafts jar directory.
  5. All scripts need to be copied into Multicrafts scripts directory,, the easiest way to do this is by running `cp -r ~/Multicraft/scripts/* /home/minecraft/multicraft/scripts/`, this moves all files from `~/Multicraft/scripts/` into Multicrafts scripts directory.
  4. Ensure these files have the correct owner by running `chown -R minecraft:minecraft /home/minecraft/multicraft/jar`, this sets the owner of all files in `/home/minecraft/multicraft/jar` to `minecraft` which is Multicrafts default user.
  5. Some configurations may require additional files to be added to Multicrafts jar directory which can be found in the [Soh.re Pulp Repo]
    * If you are running a server for a Steam game you must add steamcmd.zip, do this by running `wget https://pulp.soh.re/pulp/isos/multicraft/steamcmd.zip -O /home/minecraft/multicraft/jar/steamcmd.zip`, once again ensure the file has the correct owner by running `chown minecraft:minecraft /home/minecraft/multicraft/jar/steamcmd.zip`.
    * If you are running a server for Teamspeak you must add Teamspeak3.zip, do this by running `wget https://pulp.soh.re/pulp/isos/multicraft/steamcmd.zip -O /home/minecraft/multicraft/jar/Teamspeak3.zip`, once again ensure the file has the correct owner by running `chown minecraft:minecraft /home/minecraft/multicraft/jar/Teamspeak3.zip`.
    * If you are running a server for a Minecraft modpack open up the [Soh.re Pulp Repo] and check if there is a zip file with the corresponding name, if there is run `wget https://pulp.soh.re/pulp/isos/multicraft/{FILENAME}.zip -O /home/minecraft/multicraft/jar/{FILENAME}`, once again ensure the file has the correct owner by running `chown minecraft:minecraft /home/minecraft/multicraft/jar/{FILENAME}`.

#### 4. Setting up a Multicraft useragent
We will need to edit the Multicraft useragent so that it knows to use `prepare.sh` when starting a server, you can do this by editing `multicraft.conf`
  1. Open up `multicraft.conf` using nano (or your prefered text editor) by running `nano /home/minecraft/multicraft/multicraft.conf` and find the `useragent` configuration section
  2. Uncomment the property `userAgentDir` and set it's value to `bin`
  3. Uncomment the property `userAgentFile` and set it's value to `useragent`
  4. Uncomment the property `userAgentMinUid` and set it's value to `100`
  5. Uncomment the property `userAgentMinGid` and set it's value to `100`
  6. Uncomment the property `userAgentSuperuserPrepare ` and set it's value to `prepare.sh`
  7. Restart the Multicraft daemon to apply these changes, do this by running `/home/minecraft/multicraft/bin/multicraft stop` and then `/home/minecraft/multicraft/bin/multicraft start`

## Running
Running the server after installation is quite simple. Create a new server on Multicraft with your desired settings but the following settings must be as described:
  * The `Jar File` setting must be the server you wish to run (e.g. If this was Ark, select Steam: Ark), do __NOT__ modify the jar file name.
  * The `World` setting must be either `world` or `update` in order for the scripts to function.
  * The `Look for JARs in` setting must be `Daemon JAR directory`

[Soh.re Pulp Repo]: https://pulp.soh.re/pulp/isos/multicraft/
[Ubuntu]: https://www.ubuntu.com/
[Multicraft]: http://multicraft.org/