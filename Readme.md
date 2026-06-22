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


# ReShade

If you would also like to use ReShade with MX Bikes on Linux, follow the steps below.

## Installing ReShade

First, download the ReShade installer from:

[ReShade](https://reshade.me/#download)


After downloading the installer, add it to Steam as a **Non-Steam Game** and force it to use a Proton compatibility layer.

Launch the installer through Steam. Since ReShade will not automatically detect games installed through Proton, you will need to manually specify the path to `mxbikes.exe`.

The easiest way to find the game's installation directory is:

1. Right-click **MX Bikes** in your Steam Library.
2. Select **Properties**.
3. Open the **Installed Files** tab.
4. Click **Browse...**

This will open the MX Bikes installation directory.

For example:

```text
/home/youruser/.local/share/Steam/steamapps/common/MX Bikes/
```

Copy this path and append `mxbikes.exe` to the end:

```text
/home/youruser/.local/share/Steam/steamapps/common/MX Bikes/mxbikes.exe
```

Paste the complete path into the ReShade installer and click **Next**.

## Selecting the Rendering API

When prompted for the rendering API, select:

```text
OpenGL
```

Choosing a different API will prevent ReShade from working correctly with MX Bikes.

## Installing Shader Packages

The installer will then ask which shader packages you would like to install.

I recommend selecting all available packages. The easiest way to do this is:

1. Click **Uncheck All**.
2. Click **Uncheck All** again.

This will select every available shader package and ensure you have everything required for most ReShade presets.

Alternatively, if you already have a specific ReShade preset (`.ini` file), you can import it during installation and ReShade will automatically download only the required shader packages.

## Verifying the Installation

If the installation was successful, you should see the following file in your MX Bikes installation directory:

```text
/home/youruser/.local/share/Steam/steamapps/common/MX Bikes/opengl32.dll
```

## Steam Launch Options

Before launching the game, add the following launch option in Steam:

```bash
WINEDLLOVERRIDES="opengl32=n,b" %command%
```

To do this:

1. Right-click **MX Bikes** in Steam.
2. Select **Properties**.
3. Under **General**, locate **Launch Options**.
4. Paste the command above into the text box.

This forces Proton to use ReShade's OpenGL DLL instead of Wine's built-in implementation.

> **Note:** Tested on **CachyOS** using **Steam + Proton Experimental** on **Wayland**. Other setups may work, but are untested.

## Wayland Users

If you are using Wayland, you may also need to run MX Bikes in **Borderless Fullscreen** mode.

In my testing, ReShade would not hook correctly when using exclusive fullscreen under Wayland. Borderless fullscreen resolved the issue.

> **Note:** I have not tested ReShade under X11, so your results may vary.

