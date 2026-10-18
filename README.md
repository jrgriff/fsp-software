Instructions for installing software for the Astronomy FSP in South Africa.

# Anaconda, including Astropy
This installation is done in a Windows Subsystem for Linux terminal session.

To install conda:

curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
bash Miniforge3-$(uname)-$(uname -m).sh

The installer will prompt you to initialize `conda` for your shell, do this.

To create the astropy environment:

conda create --channel conda-forge  --name astropy python
conda activate astropy

# SAOImageDS9
DS9 can be installed both within the WSL as well as natively in Windows.  You need to install DS9 within WSL in order for it to interact with IRAF and PyRAF properly.  To install in WSL, do:

sudo apt install saods9

After ds9 has installed, type `ds9` to launch.

If you would like to install DS9 on Windows, visit https://sites.google.com/cfa.harvard.edu/saoimageds9/download to get the Windows installer.

# AstroImageJ
Visit https://astroimagej.com/#download to download the Windows version of AstroImageJ.  This software package can run natively on Windows.  The installer is hosted on a slow mirror and can take about ~10 minutes to download.

# TOPCAT
First, you will need to install Java: https://www.java.com/en/download/manual.jsp
- Try the Windows Online installer first, and use the Offline installers if you encounter problems.

Then, download the topcat-full.jar file from https://www.star.bris.ac.uk/~mbt/topcat/#standalone

To launch TOPCAT, double-click topcat-full.jar after the download has completed and choose "Allow" on any permission prompts you are presented.

# Aperture Photometry Tool
Download APT_v3.1.0.zip ("for Windows machines") from https://www.aperturephotometry.org/downloads/

You may need to accept an expired SSL certificate to reach this website.

Extract the contents of the zip file to a location that is convient for you.  APT runs from within the folder it is extracted to; navigate to that folder and double-click "APT" (the Application file, not the Batch file).

# IRAF and PyRAF

To install IRAF and PyRAF, run the following command:

sudo apt install iraf python3-pyraf python3-pyds9

# File sharing between Windows and Linux

To access files in your Linux environment from Windows, or to access files on your Windows host from within the Linux environment, follow the directions outlined here: https://learn.microsoft.com/en-us/windows/wsl/filesystems
