# Introduction #

It may take a long time before new **Frei0r plugins** are available from your distribution after they are created and supported by Flowblade.

You may want to install **Frei0r plugins** by compiling them from source code to get new functionality earlier. This is a guide how to do that, but it is provided on **"attempt at your own risk"** basis.

This guide is for Debian/Ubuntu type systems.

# Installing Frei0r plugins guide #


  1. First we need to install some stuff to be able to build Frei0r plugins:
```
sudo apt-get install git cmake libcv-dev libgavl-dev libhighgui-dev libcvaux-dev libcairo2-dev
```
  1. Create a new folder to use to build Frei0r plugins.
  1. Open terminal in the created folder.
  1. Get repository version of Frei0r
```
git clone git://git.dyne.org/frei0r.git
```
  1. Navigate to frei0r folder:
```
cd frei0r
```
  1. Give these 3 commands on terminal. Last two will take some time to complete.
```
mkdir build
cd build && cmake .. -DCMAKE_INSTALL_PREFIX=/usr && make -j3
sudo make install
```

If everything went smooth, you should now have latest plugins installed, and the related functionality should now be available in Flowblade.