
# RosProyect
## This is a University proyect to control a mobile robot using ROS, an interface should display what the sensors read and it should indicate where the robot is moving, raspberry pi must use serial communication, an xbox controller ( or any other videogame control) hast to be used to move it
Important notes


The python version used in the proyect is python 2.7
For the raspberry pi:
We are using ubiquity robotics operating system instead of rasbian due to it already has ROS installed
## Every time that the raspberry pi boots for the very fist time do the following:

You must enable the following **repositories**:
```
UNIVERSE: sudo add-apt-repository universe
MULTIVERSE:sudo add-apt-repository multiverse
RESTRICTED: sudo add-apt-repository restricted
```
Configure the locals:
```
export LC_ALL="en_US.UTF-8"
export LC_CTYPE="en_US.UTF-8"
sudo dpkg-reconfigure locales
```
A window will appear, just ignore everything and lick "ok"

To install openCV for python in the raspberry pi follow the steps from:
> https://github.com/tizianofiorenzani/how_do_drones_work/blob/master/opencv/OPENCV_INSTALL.txt

to check if everything istllaed correctly Run video.py example, the idea is to teleoperate the robot, so we must see the video from another computer.
To stream the video through ssh run the following command:
```
ssh -X user@ip_user 
```
 then run the opencv video example, and you should be able to see the video in your computer. It is importan to remember that both the raspberry pi and your computer must be connected to the same wifi
 
## Tkinter

If you don't have python then install it
> sudo apt-get install python

To make or run a interface on Tkinter its neccesary to have it installed
```
sudo apt-get install python-tk
sudo apt-get install python-imaging-tk
```
### How to use it

Open the promp of python using *promp*
Now import Tkinter module
```
>>>import Tkinter
>>>
```
To check if Tkinter was properly installed run
```
>>>Tkinter()
```
![Screenshot](Tk.png)

## In case you want to use joy_node with an xbox control(in our case)
You need to install the joy_node. You can copy and paste into your terminal:
> http://wiki.ros.org/joy/Tutorials/ConfiguringALinuxJoystick

Be careful at the moment you type the distribution, e.g. kinetic, melodic, indigo, etc
```
$ sudo apt-get install ros-indigo-joy
```
in case that ros does not found the package type the following in the terminal
```
sudo sh -c 'echo "deb http://packages.ros.org/ros-shadow-fixed/ubuntu xenial main $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

sudo apt-get install libusb-1.0-0-dev

```
Then update and finally install the joy node

## Naming the files
The standar to name an individual proyect per sensor must be
> [NameOfModule]_module
 
And the node python file
> Node_[NameOfModule]
 
The ROS master needs to have the same custom messages as the slave in order to subscribe and gather the information, the name has to be
> [NameOfModule]_data
