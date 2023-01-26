> 📜 other templates available at https://github.com/SkyrimScripting/SKSE_Templates

# SKSE "Hello, world!"

Very simple C++ SKSE plugin for Skyrim!

---

- [SKSE "Hello, world!"](#skse-hello-world)
- [What does it do?](#what-does-it-do)
- [CommonLibSSE NG](#commonlibsse-ng)
- [Requirements](#requirements)
  - [Opening the project](#opening-the-project)
- [Project setup](#project-setup)
  - [Finding Your "`mods`" Folder](#finding-your-mods-folder)
- [Setup your own repository](#setup-your-own-repository)
- [Sharing is Caring](#sharing-is-caring)

# What does it do?

After running Skyrim, once at the Main Menu, press the `~` key to open the game console.

You will see that we printed `"Hello, world!"` to the console at the Main Menu 🐉

# CommonLibSSE NG

Because this uses [CommonLibSSE NG](https://github.com/CharmedBaryon/CommonLibSSE-NG), it supports Skyrim SE, AE, GOG, and VR.

[CommonLibSSE NG](https://github.com/CharmedBaryon/CommonLibSSE-NG) is a fork of the popular [powerof3 fork](https://github.com/powerof3/CommonLibSSE) of the _original_ `CommonLibSSE` library created by [Ryan McKenzie](https://github.com/Ryan-rsm-McKenzie) in [2018](https://github.com/Ryan-rsm-McKenzie/CommonLibSSE/commit/224773c424bdb8e36c761810cdff0fcfefda5f4a).

# Requirements

- [Visual Studio 2022](https://visualstudio.microsoft.com/) (_the free Community edition_)
- [`vcpkg`](https://github.com/microsoft/vcpkg)
  - 1. Clone the repository using git OR [download it as a .zip](https://github.com/microsoft/vcpkg/archive/refs/heads/master.zip)
  - 2. Go into the `vcpkg` folder and double-click on `bootstrap-vcpkg.bat`
  - 3. Edit your system or user Environment Variables and add a new one:
    - Name: `VCPKG_ROOT`  
      Value: `C:\path\to\wherever\your\vcpkg\folder\is`

<img src="https://raw.githubusercontent.com/SkyrimDev/Images/main/images/screenshots/Setting%20Environment%20Variables/VCPKG_ROOT.png" height="150">

## Opening the project

Once you have Visual Studio 2022 installed, you can open this folder in basically any C++ editor, e.g. [VS Code](https://code.visualstudio.com/) or [CLion](https://www.jetbrains.com/clion/) or [Visual Studio](https://visualstudio.microsoft.com/)
- > _for VS Code, if you are not automatically prompted to install the [C++](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) and [CMake Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools) extensions, please install those and then close VS Code and then open this project as a folder in VS Code_

You may need to click `OK` on a few windows, but the project should automatically run CMake!

It will _automatically_ download [CommonLibSSE NG](https://github.com/CharmedBaryon/CommonLibSSE-NG) and everything you need to get started making your new plugin!

# Project setup

By default, when this project compiles it will output a `.dll` for your SKSE plugin into the `build/` folder.

If you want to configure this project to output your plugin files
into your Skyrim Special Edition's "`Data`" folder:

- Set the `SKYRIM_FOLDER` environment variable to the path of your Skyrim installation  
  e.g. `C:\Program Files (x86)\Steam\steamapps\common\Skyrim Special Edition`

<img src="https://raw.githubusercontent.com/SkyrimDev/Images/main/images/screenshots/Setting%20Environment%20Variables/SKYRIM_FOLDER.png" height="150">

If you want to configure this project to output your plugin files
into your "`mods`" folder:  
(_for Mod Organizer 2 or Vortex_)

- Set the `SKYRIM_MODS_FOLDER` environment variable to the path of your mods folder:  
  e.g. `C:\Users\<user>\AppData\Local\ModOrganizer\Skyrim Special Edition\mods`  
  e.g. `C:\Users\<user>\AppData\Roaming\Vortex\skyrimse\mods`

<img src="https://raw.githubusercontent.com/SkyrimDev/Images/main/images/screenshots/Setting%20Environment%20Variables/SKYRIM_MODS_FOLDER.png" height="150">

## Finding Your "`mods`" Folder

In Mod Organizer 2:

> Click the `...` next to "Mods" to get the full folder path

<img src="https://raw.githubusercontent.com/SkyrimDev/Images/main/images/screenshots/MO2/MO2SettingsModsFolder.png" height="150">

In Vortex:

<img src="https://raw.githubusercontent.com/SkyrimDev/Images/main/images/screenshots/Vortex/VortexSettingsModsFolder.png" height="150">

# Setup your own repository

If you clone this template on GitHub, please:

- Go into `LICENSE` and change the year and change `<YOUR NAME HERE>` to your name.
- Go into `CODE_OF_CONDUCT.md` and change `<YOUR CONTACT INFO HERE>` to your contact information.

The `LICENSE` defaults to using the [MIT License](https://choosealicense.com/licenses/mit/), a permissive license which is used by many popular Skyrim mods (_including [CommonLibSSE](https://github.com/Ryan-rsm-McKenzie/CommonLibSSE)_).

The `CODE_OF_CONDUCT.md` defaults to using the [Contributor Covenant](https://www.contributor-covenant.org/), the most popular code of conduct for open source communities.

If you'd like to know more about open source licenses, see:
- [Licensing a repository](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository)
- [Choose an open source license](https://choosealicense.com/)

# Sharing is Caring

**If you use this template, PLEASE release your project as a public open source project.** 💖

**Please do not release your SKSE plugin on Nexus/etc without making the source code available** \*

> \* _You do you. But please help our community by sharing your source `<3`_
