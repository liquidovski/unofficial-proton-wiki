# Known workarounds
This page contains known workarounds for issues such as a Linux Runtime 3.0 issue on older NVIDIA GPUs and NTFS read errors on Proton.

## Old NVIDIA GPU Runtime workaround
If you have an older NVIDIA GPU, games running through Proton will most likely not launch due to a runtime issue. (https://github.com/ValveSoftware/steam-runtime/issues/420)

To work around this issue, go to your Steam Library, find `Steam Linux Runtime 3.0 (Sniper)`, right click on it, hover onto `Manage` and press `Browse local files` and replace the file named `_v2-entry-point` with the file at this [link](https://drive.usercontent.google.com/download?id=1tTyTwkh1uIbrpjLfLnKJry4AJDsdyA1m&export=download&authuser=0)

## NTFS Read Error workaround

**THERE HAS BEEN A REPORT THAT THIS MAY CAUSE DATA LOSS, DO THIS AT YOUR OWN RISK**

Due to the nature of NTFS, creating files/folders with characters Windows cannot read will cause disk errors (leading to games that don't launch), the most common issue is a character in filenames that Proton creates on the NTFS disk.

Fixing this is pretty simple. Create a symlink from the /compatdata folder on Linux to the mounted NTFS disk. In this example we will assume that your NTFS partition is mounted to /media/gamedisk/, please change it accordingly.

Creating the symlink (edit ``/media/gamedisk/Steam/steamapps/`` to your actual mount point):

```
mkdir -p ~/.steam/steam/steamapps/compatdata
rm -rf /media/gamedisk/Steam/steamapps/compatdata
ln -s ~/.steam/steam/steamapps/compatdata
```

[Source](https://github.com/ValveSoftware/Proton/wiki/Using-a-NTFS-disk-with-Linux-and-Windows#preventing-ntfs-read-errors)
