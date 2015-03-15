# Introduction #

It may be useful to test the repository version of the application, for example when testing bug fixes for issues that are not visible in the development systems.

This installation does not affect the .deb installed stable version, **except** for changes in editor Preferences or user created Profiles. Both versions use the same location to save this data.

It is not recommended to use repository version for actual editing work.


# Installing from repository #
This guide is for Debian/Ubuntu type systems.

  1. Install Mercurial. Mercurial is a source version control program used here to download repository version of Flowblade. Open terminal and give command:
```
sudo apt-get install mercurial
```
  1. Create a new folder for repository version of Flowblade.
  1. Open terminal in the created folder.
  1. Get repository version of Flowblade using Mercurial.
```
hg clone https://code.google.com/p/flowblade/
```
  1. Navigate to application folder
```
cd flowblade/flowblade-trunk/
```
  1. Launch Flowblade
```
./flowblade 
```
  1. Repository version can only be launched from the application directory, with command ./flowblade. Using command flowblade anywhere else will launch the installed version of the application, or complain that the command was not found.

When you're running the repository version lauched with terminal, the first two lines should have word repository in them, something like:
```
FLOWBLADE MOVIE EDITOR 0.13 repository
--------------------------------------
```