# SODA.Sim ROS2 Workspase
This repository contains scripts for build ROS2 for [SODA.Sim ROS2](https://github.com/soda-auto/soda-sim-ros2) for Windows and Linux.  

## For for Windows
We don't build ROS2 from source for Windows. We use official prebuiled releases from [here](https://github.com/ros2/ros2/releases). 
  - Perfom all step from [Original Manuale](https://docs.ros.org/en/humble/Installation/Windows-Install-Binary.html#) till to [environment-setup](https://docs.ros.org/en/humble/Installation/Windows-Install-Binary.html#environment-setup).  
    [Downloading ROS-2](https://docs.ros.org/en/humble/Installation/Windows-Install-Binary.html#downloading-ros-2) to the *SODA_SIM_ROS2/ros2-windows* folder.  
    Note: You can skip "Install OpenCV", "Install Qt5", "RQt dependencies" steps from the manul.
  - Open *x64 Native Tools Command Prompt for VS 2022*
  - Build and install the [ackermann_msgs](https://github.com/ros-drivers/ackermann_msgs/tree/ros2) to the *ros2-windows* folder:
    ```
    $ call <SODA_SIM_ROS2>/ros2-windows/setup.bat
    $ cd <ACKERMAN_MSGS_ROOT>
    $ colcon build --merge-install
    $ cp -a <ACKERMAN_MSGS_ROOT>/Install/. <SODA_SIM_ROS2>/ros2-windows/
    ```

## For Linux 
Tested on Ubuntu 22.04 only.  
  - Perfom all step from [Original Manuale](https://docs.ros.org/en/humble/Installation/Alternatives/Ubuntu-Development-Setup.html) till to [Install additional DDS implementations (optional)](https://docs.ros.org/en/humble/Installation/Alternatives/Ubuntu-Development-Setup.html#id8).
  - Remove *./src/eclipse-cyclonedds* and *./src/eclipse-iceoryx* folders
  - Build ROS2:
    ```
	$ export UE_ENGINE=<PATH_TO_UNREAL_ENGINE>/Engine
	$ ./vcpkg-linux.sh
	$ ./BuildForLinux.sh
	$ cp -a Install/. <REPO_ROOT>/ros2-linux/
	```
  - Build and install the [ackermann_msgs](https://github.com/ros-drivers/ackermann_msgs/tree/ros2) to the *ros2-linux* folder:
    ```
    $ source <REPO_ROOT>/ros2-linux/setup.bash
	$ export UE_ENGINE=<PATH_TO_UNREAL_ENGINE>/Engine
    $ cd <ACKERMAN_MSGS_ROOT>
    $ colcon build --merge-install --cmake-args -DCMAKE_TOOLCHAIN_FILE=<REPO_ROOT>/unreal-linux-toolchain.cmake
    $ cp -a <ACKERMAN_MSGS_ROOT>/Install/. <SODA_SIM_ROS2>/ros2-linux/
    ```
