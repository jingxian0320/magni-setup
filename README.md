# Set-up Guide for Ubiquity Magni Robot

1. Connet to the Robot 
1.1 First-time setup
- Follow the [guide](https://learn.ubiquityrobotics.com/connecting) 
1.2 if it is set up previously to connet to the wifi
- connect to the same wifi
- ssh ubuntu@IP-ADDRESS (default pw: ubuntu)

2. Setup the workstation
- load the [VM image](https://downloads.ubiquityrobotics.com/vm.html) into the VirtualBox
- follow the [guide](https://learn.ubiquityrobotics.com/workstation_setup) and could skip the parts about zeroconf networking and set the environment variables using IP if connecting to the same wifi (not robot hotspot). 
- follow the guide [here](https://learn.ubiquityrobotics.com/simulation) to install catkin
- install the package [teleop_twist_keyboard](https://answers.ros.org/question/199363/error-run-teleop_twist_keyboard-package/) to drive from the workstation. 

3. Setup rpRidar
- follow the [guid]e(https://learn.ubiquityrobotics.com/lidar_navigation). The edit of node.cpp is not needed as it should no longer exist in the current repo.
- If 'Error, cannot bind to the specified serial port /dev/ttyUSB0'
  - check the location of the RPlidar serial port with `ls -l /dev|grep ttyUSB`
  - check if cp210x is active using `lsmod`
  - check if cp210x is available in the system using `ls -al /lib/modules/"$(uname -r)"/kernel/drivers/usb/serial/cp210x.ko`
  - `sudo apt-get install build-essential linux-source` might work to resolve the problem followed by a **reboot**
  - if encountering access problem, `sudo chmod 666 /dev/ttyUSB0`
- additional [reference](https://medium.com/robotics-with-ros/installing-the-rplidar-lidar-sensor-on-the-raspberry-pi-32047cde9588)

## Hint
- If anything weried happens, try to turn it off and on again:) [**with clean shutdown**](https://learn.ubiquityrobotics.com/connecting)
