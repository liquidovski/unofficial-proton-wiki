# What is this page?

This page contains things you can do on your own when trying to troubleshoot a game running through Proton.

# Try a different proton version

At the time of writing, Proton 8.0-4 is the default proton version being used so when you click "PLAY" on a game on Steam, that version will be used. To override the default Proton version, Right-click on the game in your library, go to `Properties` then find the `Compatibility` tab, click that and select `Force the use of a specific Steam Play compatibility tool`, then select the proton release you want to use.

# Try a custom proton version

Since Proton is an open source project, forks of proton exist but when a "custom proton version" is mentioned, most of the time people are referring to [Proton-GE](https://github.com/GloriousEggroll/proton-ge-custom), so I will first explain ways to install Proton-GE and tools related to it.

## protonup (recommended)

From protonup's github page:

"CLI program and API to automate the installation and update of GloriousEggroll's Proton-GE"

to use protonup, get it from your distro's repo or compile from source. Unless you Installation instructions can be found at [protonup's github repo](https://github.com/AUNaseef/protonup#installation)

Usage: simply type `protonup` into your terminal when you want to fetch the latest release of Proton-GE

## protonup-qt

protonup-qt is basically just a version of protonup with a user interface that uses the qt framework. (Don't worry, you don't need to know what a framework is to understand or use this program :P)

to use protonup-qt, get it from your distro's repo, compile from source or [use the flatpak](https://flathub.org/apps/net.davidotek.pupgui2). Installation instructions can be found at [protonup-qt's github repo](https://github.com/DavidoTek/ProtonUp-Qt#install-from-aur-arch-manjaro-endeavouros-etc)

Usage:

- Look for the ProtonUp-Qt desktop item in your applications menu.

-Type `protonup-qt` into your terminal.

Flatpak usage:

- Look for the ProtonUp-Qt desktop item in your applications menu.

- If you are using the flatpak, type `flatpak run net.davidotek.pupgui2` into your terminal.

then select `Steam` and click `Add version` and select `GE-Proton` under `Compatibility tool` to install Proton-GE

## Manual

This method should work for all custom proton builds, you simply need to put your proton build inside `~/.steam/root/compatibilitytools.d/`. Make sure that the proton build you are trying to use is not in archive formats like `.zip`, `.tar.gz` and so on or else Steam won't be able to read the contents so make sure to extract it beforehand.
