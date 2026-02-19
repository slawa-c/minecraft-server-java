# Minecraft Java Edition — Server Assets and Tools

Purpose
- **Purpose:** This folder holds maps, resource packs, plugins and helper applications organized by Minecraft Java Edition version to support hosting a self-made Minecraft server.

Repository structure
- **Top-level:** Contains versioned subfolders and an `app/` folder for helper applications.
- **Version folders:** Each versioned folder (for example [v1.13.2/](v1.13.2/), [v1.16.5/](v1.16.5/), [v1.21.11/](v1.21.11/)) groups assets compatible with that Minecraft release:
  - **Maps:** World saves and map folders to copy into a server's `world` directory.
  - **resourcepacks:** Client or server resource packs tuned to that version.
  - **plugins:** (If present) Plugin jars compatible with server software for that version.
- **app/**: Applications and installers (tools you use on the hosting machine or client).

## minecraft 1.16.5

```bash
sudo apt-get install -y java-16-amazon-corretto-jdk
sudo apt-get install -y java-1.8.0-amazon-corretto-jdk
```

## minecraft 1.21.11

```bash
sudo apt-get install -y java-21-amazon-corretto-jdk libxi6 libxtst6 libxrender1
```

```bash
curl -kLJ https://fill-data.papermc.io/v1/objects/838a59ce982cd3b919afeea677977d1b267f7fddd3fcf9c186a63c33896dff02/paper-1.21.11-112.jar -o paper-1.21.11-112.jar

screen -S PirateBay java -Xms4G -Xmx4G -jar paper-1.21.11-112.jar --nogui
java -Xms4G -Xmx4G -jar paper-1.21.11-112.jar --nogui
```

## set desired java versions

Minecraft 1.16.x supports only Java v8.x or Java v16.x, to run this version you need to switch supported Java runtime version.

```bash
sudo update-alternatives --config java
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                                  Priority   Status
------------------------------------------------------------
* 0            /usr/lib/jvm/java-21-amazon-corretto/bin/java          12100007  auto mode
  1            /usr/lib/jvm/java-1.8.0-amazon-corretto/jre/bin/java   10800482  manual mode
  2            /usr/lib/jvm/java-21-amazon-corretto/bin/java          12100007  manual mode

Press <enter> to keep the current choice[*], or type selection number: 1
update-alternatives: using /usr/lib/jvm/java-1.8.0-amazon-corretto/jre/bin/java to provide /usr/bin/java (java) in manual mode
```

```bash
curl -kLJ https://fill-data.papermc.io/v1/objects/e67da4851d08cde378ab2b89be58849238c303351ed2482181a99c2c2b489276/paper-1.16.5-794.jar -o paper-1.16.5-794.jar

screen -r PirateBay java -Xms4G -Xmx4G -jar paper-1.16.5-794.jar --nogui
java -Xms4G -Xmx4G -jar paper-1.16.5-794.jar --nogui
```

## check java

```bash
java -version
```

Quick usage
- **Choose a version:** Pick the version folder matching the server jar you run (e.g., Paper/Spigot for 1.21.11 → use `v1.21.11/`).
- **Install a map:** Copy a map folder from `.../Maps/` into your server directory and rename it to `world` (or set `level-name` in `server.properties`). Example:

```
cp -R v1.21.11/Maps/MyMap /path/to/minecraft-server/world
```

- **Add resource packs:** Place packs into your server or distribute to clients. For server-side forced packs, see your server software docs (e.g., Paper `server.properties` `resource-pack` settings).
- **Install plugins:** Drop compatible `.jar` files into your server's `plugins/` folder and restart the server.

Running a server (example)
- **Accept EULA:** Create `eula.txt` with `eula=true` in the server root (or start the server once and edit the generated file).
- **Start (Paper/Spigot example):**

```
java -Xms1G -Xmx4G -jar paper-1.21.11.jar nogui
```

Backups & maintenance
- **Backup world:**

```
zip -r backups/world-$(date +%F).zip world
```

- **Keep compatibility:** Use plugins and resource packs that match your chosen server and protocol version.

Notes & recommendations
- **Server software:** For best performance and plugin compatibility, prefer Paper (or Purpur) builds matching the Minecraft version.
- **Client packs:** Resource packs in this repo are for convenience; instruct players to install them client-side when required.
- **Applications in `app/`:** Tools here (DMGs, installers) are utilities for managing mods/clients—use them on your machine, not directly on the headless server.

Want scripts or automation?
- If you'd like, I can add small helper scripts to automate map installation, backups, or start/stop commands. Tell me which server version and automation you'd prefer.

License & usage
- **Personal use:** This repo is arranged for your private server hosting; verify any third-party plugin or pack licenses before redistribution.
