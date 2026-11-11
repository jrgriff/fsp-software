# Astronomy FSP in South Africa Software Installation (macOS)

This document provides instructions on how to install required software on a Mac.  Instructions are provided for both Apple Silicon (M-series) and Intel Macs; most steps are the same for both.

## Table of contents
1. [Homebrew and XQuartz](#homebrew-and-xquartz)
2. [conda/mamba and astropy](#condamamba-and-astropy)
3. [Jupyter Notebook](#jupyter-notebook)
4. [SAOImageDS9](#saoimageds9)
5. [TOPCAT](#topcat)
6. [AstroImageJ](#astroimagej)
7. [Aperture Photometry Tool](#aperture-photometry-tool)
8. [IRAF and PyRAF](#iraf-and-pyraf)
9. [Opening apps from unidentified developers](#opening-apps-from-unidentified-developers)
10. [Additional documentation](#additional-documentation)


## Homebrew and XQuartz
Most of this installation is done in the __Terminal__ app (in __Applications__ → __Utilities__).  *`$` indicates a terminal prompt; you do not need to type the `$`, only the command that follows. The __Copy__ button on each box copies just the commands.*

[Homebrew](https://brew.sh) is a package manager for macOS, and is used below to install IRAF and Java.  **To install Homebrew**, run the following command and follow the prompts.  It will ask for your Mac password, and will also install Apple's Command Line Tools if you do not already have them:

```console
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

At the end of the installation, Homebrew prints a few commands under __Next steps__ that add `brew` to your shell; copy and run those, then close and re-open Terminal.

**To install [XQuartz](https://www.xquartz.org)**, an X11 server needed by some of the IRAF tools:

```console
$ brew install --cask xquartz
```

*After installing XQuartz for the first time you must log out and back in (or restart your Mac).*

## conda/mamba and astropy
For the purposes of this guide, you will be installing [Miniforge](https://github.com/conda-forge/miniforge), a lightweight version of conda that also provides [`mamba`](https://mamba.readthedocs.io/en/latest/), a faster version of conda.

**To install [Miniforge](https://github.com/conda-forge/miniforge#unix-like-platforms-macos-linux--wsl):**

```console
$ curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
$ bash Miniforge3-$(uname)-$(uname -m).sh
```

The installer may prompt you to initialize conda for your shell; do this, and then also do `mamba init`.  Close and re-open Terminal afterwards.

**To create the [astropy](https://www.astropy.org) environment:**

```console
$ mamba create --channel conda-forge  --name astropy python
$ mamba activate astropy
$ mamba install --channel conda-forge scipy matplotlib
```

To activate the `astropy` environment in the future (for example, if you have just opened a new Terminal window), type `mamba activate astropy`

## Jupyter Notebook
[Jupyter Notebook](https://jupyter.org) lets you run Python interactively in your web browser.  **To install it** into the `astropy` environment:

```console
$ mamba activate astropy
$ mamba install --channel conda-forge notebook
```

**To launch Jupyter Notebook**, open Terminal and do:

```console
$ mamba activate astropy
$ cd ~
$ jupyter notebook
```

Jupyter will open in your default web browser.  If it does not, copy the link it prints that looks like `http://localhost:8888/tree?token=...` and paste the whole link into your browser.  Notebooks you create are saved in the folder you were in when you launched Jupyter; `cd ~` starts it in your home folder.

Leave the Terminal window open while you are using Jupyter.  When you are finished, save your notebooks, go back to Terminal and press __Control__+__C__ twice to shut Jupyter down.

## SAOImageDS9
Visit <https://sites.google.com/cfa.harvard.edu/saoimageds9/download> and, under __macOS__, download the __macOS 12+ (Universal)__ version (not the X11 one).  Open the downloaded `.dmg` file and drag __SAOImageDS9__ into your __Applications__ folder.

Launch __DS9__ from __Applications__ or Launchpad.  If macOS refuses to open it, see [Opening apps from unidentified developers](#opening-apps-from-unidentified-developers).

## TOPCAT
**To install [TOPCAT](https://www.star.bris.ac.uk/~mbt/topcat/)** with Homebrew:

```console
$ brew install --cask topcat
```

*Alternatively, download `topcat-all.dmg` from <https://www.star.bris.ac.uk/~mbt/topcat/#install>, open it and drag __TOPCAT__ into your __Applications__ folder.*

Either way, TOPCAT includes its own copy of Java, so you do not need to install Java separately for it.  Launch __TOPCAT__ from __Applications__ or Launchpad.

## AstroImageJ
Visit <https://astroimagej.com/#download> and download the __Mac (Arm)__ version if you have an Apple Silicon (M-series) Mac, or __Mac (Intel)__ for an older Intel Mac.  *To check which you have, open the Apple menu → __About This Mac__ and look at the __Chip__ or __Processor__ line.*

The download is hosted on a slow mirror and can take about ~10 minutes.  Open the downloaded file, drag __AstroImageJ__ into your __Applications__ folder, and launch it from there.

## Aperture Photometry Tool
__APT__ is a Java program and needs Java 13 or newer.  **To install Java:**

```console
$ brew install --cask temurin
```

Then download `APT_v3.1.0.dmg` ("Mac, regular-sized GUI") from <https://www.aperturephotometry.org/downloads/>

You may need to accept an expired SSL certificate to reach this website.

Open the downloaded `.dmg` file and drag __APT__ into your __Applications__ folder, then launch it from there.

## IRAF and PyRAF
**To install [IRAF](https://iraf-community.github.io)** (this also installs `xgterm` and `ximtool`, which use XQuartz):

```console
$ brew tap iraf-community/tap
$ brew trust iraf-community/tap
$ brew install iraf x11iraf
```

**To install PyRAF and pyds9** into the `astropy` environment:

```console
$ mamba activate astropy
$ pip install pyraf pyds9
```

To launch IRAF type `ecl`.  To launch PyRAF, activate the `astropy` environment and type `pyraf`.  Start __DS9__ before displaying images from IRAF or PyRAF.

## Opening apps from unidentified developers
Some of these programs are not signed by Apple, and the first time you open one macOS may say that it "cannot be opened" or "cannot verify the developer".  To open it anyway:

1. Try to open the app once and dismiss the warning.
2. Open __System Settings__ → __Privacy & Security__ and scroll down to __Security__.
3. Click __Open Anyway__ next to the message about the app, and confirm with your password.

You only need to do this once for each app.

## Additional documentation

- [Getting started with the Mac Terminal](https://support.apple.com/guide/terminal/welcome/mac)
- [Managing conda environments](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)
- [Homebrew documentation](https://docs.brew.sh)
- [IRAF Community Distribution](https://iraf-community.github.io)
