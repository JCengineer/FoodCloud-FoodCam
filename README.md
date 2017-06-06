# FoodCloud-FoodCam

If you have surplus food to share with the office
put the food on the table
point the camera at it
press the button!

Everyone in the office will automatically get a picture of the food sent to them (via slack, if you don’t have it, get it…slack.com) to say there’s food available!


#####################################
## Set up FoodCam
#####################################

#####################################
## Headless Setup of Pi
## Download latest version of Raspian Jessie Lite from https://www.raspberrypi.org/downloads/raspbian/
# Install Raspbian Jessie Lite on SD Card with Etcher

# Create blank file called 'ssh' and add to boot partition
# Create file called 'wpa_supplicant.conf' and add to boot partition

network={
ssid="NETWORK NAME"
psk="PASSWORD"
key_mgmt=WPA-PSK
}

#####################################
# 1st boot
#####################################
#Locate On Network, default hostname is raspberrypi
sudo passwd
# Follow Instructions to change password


#####################################
# Change raspi-config 
#####################################
sudo raspi-config
# Follow dialog to enable camera and change hostname to foodcam

#####################################
# Update Image
#####################################
sudo apt-get update
sudo apt-get upgrade
# Make some coffee - takes a bit of time!
sudo apt-get install motion


#####################################
# Install Motion
#####################################
sudo apt-get install motion

sudo nano /etc/rc.local

# before exit=0 type:
modprobe bcm2835-v4l2

sudo nano /etc/default/motion
# set to yes

#####################################
# Update motion.conf
#####################################

sudo nano /etc/motion/motion.conf

daemon on

# width 1024
# height 576

# output_pictures off
# ffmpeg_output_movies off

# target_dir /home/pi/motion

stream motion on
stream_localhost off
