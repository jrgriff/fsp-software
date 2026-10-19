# Astronomy FSP in South Africa Software Installation

This document provides instructions on how to install required software.  Instructions provided are for [Ubuntu](https://ubuntu.com/wsl/docs/stable/howto/install-ubuntu-wsl2/) installed under the [Windows Subsystem for Linux](https://learn.microsoft.com/en-us/windows/wsl/install) (__WSL__).

## Table of contents
1. [conda/mamba and astropy](#conda-mamba-and-astropy)
2. [SAOImageDS9](#saoimageds9)
3. [AstroImageJ](#astroimagej)
4. [TOPCAT](#topcat)
5. [Aperture Photometry Tool](#aperture-photometry-tool)
6. [IRAF and PyRAF](#iraf-and-pyraf)
7. [File sharing between Windows and Linux](#file-sharing-between-windows-and-linux)
8. [Additional documentation](#additional-documentation)


## conda/mamba and astropy
This installation is done in a WSL terminal.  *`$` indicates a Linux prompt; you do not need to re-type the `$`, only the command that follows.*

For the purposes of this guide, you will be installing [Miniforge](https://github.com/conda-forge/miniforge), a lightweight version of `conda` that also provides [`mamba`](https://mamba.readthedocs.io/en/latest/), a faster version of `conda`.

**To install [Miniforge](https://github.com/conda-forge/miniforge#unix-like-platforms-macos-linux--wsl):**

```
$ curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
$ bash Miniforge3-$(uname)-$(uname -m).sh
```

The installer may prompt you to initialize `conda` for your shell; do this, and then also do `mamba init`.

**To create the astropy environment:**

```
$ mamba create --channel conda-forge  --name astropy python
$ mamba activate astropy
$ mamba install --channel conda-forge scipy matplotlib
```

To activate the `astropy` environment in the future (for example, if you have just started a new WSL session), type `mamba activate astropy`

## SAOImageDS9
**DS9** can be installed both within the WSL as well as natively in Windows.  You need to install DS9 within WSL in order for it to interact with IRAF and PyRAF properly.  To install in WSL, do:

```
sudo apt install saods9
```

After DS9 has installed, type `ds9` to launch.

*If you would like to install DS9 on Windows, visit <https://sites.google.com/cfa.harvard.edu/saoimageds9/download> to get the Windows installer.*

## TOPCAT
First, you will need to install Java: <https://www.java.com/en/download/manual.jsp>
- *Try the Windows Online installer first, and use the Offline installers if you encounter problems.*

Then, download the `topcat-full.jar` file from <https://www.star.bris.ac.uk/~mbt/topcat/#standalone>

To launch __TOPCAT__, double-click `topcat-full.jar` after the download has completed and choose "Allow" on any permission prompts you are presented.

## AstroImageJ
Visit <https://astroimagej.com/#download> to download the Windows version of __AstroImageJ__.  

This software runs natively on Windows using the same Java runtime that was installed for TOPCAT.  The installer is hosted on a slow mirror and can take about ~10 minutes to download.  Open the downloaded installer and use the defaults it offers you.  `AstroImageJ` will be available in your __Start__ menu on Windows after installation.

## Aperture Photometry Tool
Download `APT_v3.1.0.zip` ("for Windows machines") from <https://www.aperturephotometry.org/downloads/>

You may need to accept an expired SSL certificate to reach this website.

Extract the contents of the zip file to a location that is convient for you.  __APT__ is also a Java program and runs from within the folder it is extracted to; navigate to that folder and double-click `APT` (there bay also be an `APT.bat` file that can be ignored).

## IRAF and PyRAF

To install __IRAF__ and __PyRAF__, run the following command in a WSL terminal:

```
$ sudo apt install iraf python3-pyraf python3-pyds9
```

To launch IRAF you will need to type `irafcl`.  To launch PyRAF type `pyraf`.

## File sharing between Windows and Linux

To access files in your Linux environment from Windows, or to access files on your Windows host from within the Linux environment, follow the directions outlined here: <https://learn.microsoft.com/en-us/windows/wsl/filesystems>

## Additional documentation

- [Getting started with Linux and bash on WSL](https://learn.microsoft.com/en-us/windows/wsl/tutorials/linux)
- [Managing conda environments](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)
- [Setting up a WSL development environment](https://learn.microsoft.com/en-us/windows/wsl/setup/environment)
- [IRAF Community Distribution](https://iraf-community.github.io)
