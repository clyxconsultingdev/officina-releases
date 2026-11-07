# Officina releases

Builds of Officina, a Minecraft mod that makes a live office for coding agents. The source is private; this repo holds only what Prism Launcher needs to keep the mod up to date by itself.

Set up an instance once, and from then on, whenever the game starts, Prism checks for a new version and downloads it, checking every file against its checksum. Nobody sends jars around.

## Setting up Prism, once

You need a Prism Launcher instance for Minecraft 26.2 with Fabric. If you're joining someone's world, also add Essential, as they told you.

1. **Download the two updater files**, and put them in the instance's `minecraft` folder: in Prism, right-click the instance → **Folder**, then open `minecraft` (on some systems it's `.minecraft`).
   - [packwiz-installer-bootstrap.jar](https://raw.githubusercontent.com/clyxconsultingdev/officina-releases/main/setup/packwiz-installer-bootstrap.jar)
   - [packwiz-installer.jar](https://raw.githubusercontent.com/clyxconsultingdev/officina-releases/main/setup/packwiz-installer.jar)
2. **Remove any Officina jar you added by hand** from the instance's `mods` folder, such as `officina-0.1.0.jar`. From now on the updater puts it there, and two copies would stop the game from starting. Keep Essential, and anything else that isn't Officina or Fabric API.
3. **Add the update check:** right-click the instance → **Edit** → **Settings** → **Custom commands**, tick **Custom commands**, and paste this into **Pre-launch command**, as one line:

   ```
   "$INST_JAVA" -jar "$INST_MC_DIR/packwiz-installer-bootstrap.jar" --bootstrap-no-update --bootstrap-main-jar "$INST_MC_DIR/packwiz-installer.jar" https://raw.githubusercontent.com/clyxconsultingdev/officina-releases/main/pack.toml
   ```

4. **Close the window and press Play.** A small window shows the download the first time, then the game starts.

## Afterwards

Just press Play. When there's a new version, the small window shows for a moment while it downloads. A version reaches everyone within 5 minutes of being released; start the game before then and you keep the one you had, until the next start. Both players need the same version to play together, so if one of you was already in the game when a version came out, restart it.

If something goes wrong, the small window says what. To stop updating, untick **Custom commands**.

## What gets installed

`pack.toml` lists the mods, each with its checksum, in `mods/`: Officina, from this repo's releases, and Fabric API, from Modrinth. The updater is [packwiz-installer](https://github.com/packwiz/packwiz-installer) (MIT licence), pinned to v0.5.14, with its bootstrap v0.0.3, so nothing changes under you without a release here.
