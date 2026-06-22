# Installing Mods on Linux

This guide will show you how to install mods for MX Bikes on Linux, as well as how to install ReShade.

## Locating the MX Bikes Mod Folder

To install mods, you first need to locate MX Bikes' Proton compatibility data folder (`compatdata`).

The easiest way to find it is through Steam:

1. Right-click **MX Bikes** in your Steam Library.
2. Select **Properties**.
3. Open the **Updates** tab.
4. Note the **App ID** listed for the game.

For MX Bikes, the App ID is:

```text
655500
```

This App ID corresponds to the game's `compatdata` folder.

On most systems, the `compatdata` directory can be found at:

```text
~/.local/share/Steam/steamapps/compatdata/
```

If Steam is installed elsewhere, navigate to your Steam installation directory and locate the `compatdata` folder there.

## Installing Mods

Once you have located the `compatdata` directory, navigate to:

```text
655500/pfx/drive_c/users/steamuser/Documents/PiBoSo/MX Bikes/mods/
```

Or, using the default Steam location:

```text
~/.local/share/Steam/steamapps/compatdata/655500/pfx/drive_c/users/steamuser/Documents/PiBoSo/MX Bikes/mods/
```

Inside the `mods` folder you will see directories such as:

```text
bikes/
rider/
tracks/
tyres/
```

Different mods belong in different folders, so always check the README or installation instructions provided with the mod you downloaded.

## Creating a Symlink (Recommended)

If you plan on installing mods regularly, creating a symbolic link (symlink) can make managing your mods much easier.

A symlink allows you to access the MX Bikes mod directory from a more convenient location without having to navigate through the full Proton directory structure every time.

You can create a symlink using:

```bash
ln -s "<path-to-mods-folder>" "<desired-symlink-location>"
```

For example:

```bash
ln -s \
"~/.local/share/Steam/steamapps/compatdata/655500/pfx/drive_c/users/steamuser/Documents/PiBoSo/MX Bikes/mods" \
"~/Modding/MX Bikes Mods"
```

After creating the symlink, you can access your MX Bikes mods directly from:

```text
~/Modding/MX Bikes Mods
```

This can save a lot of time when installing or updating mods.

