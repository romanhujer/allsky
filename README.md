# Allsky Camera

This is the source code for the Wireless Allsky Camera project described [on Instructables](http://www.instructables.com/id/Wireless-All-Sky-Camera/).


## Requirements

In order to get the camera working properly you will need the following hardware:

 * An ASI camera from ZWO. Tested cameras include ASI120MC, ASI224MC
 * A Raspberry Pi 2 or 3
 * A USB wireless dongle if using a Pi 2. [This one](https://www.amazon.ca/Edimax-EW-7811Un-150Mbps-Raspberry-Supports/dp/B003MTTJOY) has been tested.

## Installation

You will need to install Raspbian on your Raspberry Pi. Follow [this link](https://www.raspberrypi.org/documentation/installation/installing-images/) for information on how to do it.

Make sure you have a working internet connection by setting it either through the GUI or [the terminal](https://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md). 

If you are running a lite version of Raspbian, you probably don't have git yet. Install it now:

```shell
sudo apt-get install git
```

Now fetch the code from this GitHub page. Open the terminal and type the following:

```shell
git clone https://github.com/thomasjacquin/allsky.git
```

Then navigate to the allsky directory:

```shell
cd allsky
```

Now, run the install script:

```shell
sudo ./install.sh
```

**Important**: Unplug and replug the camera to trigger the new udev rules otherwise you'll get an error about permissions later.

## Usage

You can now start the camera by typing the following:

```shell
./capture
```
An example of how to use it is:
```shell
./capture -width 640 -height 480 -exposure 5000000 -gamma 50 -type 1 -bin 1 -filename "observatory-site.PNG"
```

For a full list of available arguments, run:
```shell
./capture -help
```

In order to make things a little easier, you can edit allsky.sh, modify the options by passing or removing arguments and run the script:
```shell
./allsky.sh
```
It will do the same thing as "capture" but you won't have to re-type all the arguments everytime.

## Usage without GUI

**Note**: If you're using Raspbian lite or another distribution without desktop environment, make sure to use the following argument:
```shell
-nodisplay 1
```

If you are running Raspbian with LXDE or Pixel, you can set this argument to 0 or remove it entirely to get a live view from the camera while it's saving the images.
```shell
-nodisplay 0
```
