<a href="https://www.buymeacoffee.com/thibaut_watrisse" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" alt="Buy Me A Coffee" height="41" width="174"></a>

# Minecraft_Local_Docker
Docker-compose to launch a Minecraft LAN

## Requirements 

Firstly, modify the following of the docker-compose :

````bash
- MEMORY=8G # set the RAM memory you allow the docker to use
- VERSION=1.20.1 # The Minecraft version you want to use
- FORGE_INSTALLER=forge-1.20.1-47.2.17-installer.jar # The installer you will use
````

After that, please download the installer you want to use (in the current example, forge-1.20.1-47.2.17-installer.jar).

Find your version in this website for example -> https://files.minecraftforge.net/net/minecraftforge/forge/index_1.20.1.html

After that, download the file, create a repository called "minecraft" (warning it's case sensitive) at the same level then the yaml file and move the .jar file to the Minecraft repository.

### Linux

update packages and install docker 

````bash
sudo apt update -y && sudo apt upgrade -y
sudo apt install docker.io docker-compose -y
sudo usermod -aG docker <current_user>
su <current_user>
docker-compose up
````

````bash
docker-compose up
````

### Windows

Install docker desktop and run the container using :

````bash
docker-compose up
````

## Run to docker

Run the server with the following :

````bash
docker-compose up -d
````

## Firewall

As you specified the port 25564 to be joinable for your Minecraft server, please ensure that you authorize connections to this port in your firewall settings.

## Download Minecraft

To join the server, you should download Minecraft launcher (if you don't have official, you can try via Tlauncher -> https://tlauncher.org/en/). Once in, please be sure you run the correct version you specified in the yaml file. 

## Server access

Onece done, the server will be joinable with the IP address of the serveur with the port 25564. Verify that this port is open in your firewall settings.
So in the Minercraft launcher, you should quick join and specify <ServerIp>:<ServerPort> (here the port is 25564).

## Minecraft commands

You can use docker exec -it minecraft rcon-cli to exec Minecraft commands (For Example) :

````bash
/op <player> - Update a player to admin
/give <player> <item> - Give an item to another player
/gamemode <mode> - Change game mode
/tp <player> - TP to another player
/list - Connected user list
````

You can use the following to exec Minecraft container and exec commands (for example /op <username> to add an admin) : 

````bash
docker exec -it minecraft rcon-cli
````

## Add some mods

Put your mod files (like cfm-forge-1.20.1-7.0.0-pre36.jar)) in the ~/minecraft/mods repository.

## Issues 

If you get an issue cause of docker rights, please try to run the container in sudo mode or correct the repository access rights.

## Sources

- https://johackim.com/installer-un-serveur-minecraft-avec-docker
