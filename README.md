# QGroundControl - Getting Started

This guide provides step-by-step instructions for obtaining the QGroundControl source code, building it natively, or within a Vagrant environment. It also covers optional and OS-specific functionality.

## Daily Builds

If you only need to test a recent QGroundControl build without debugging, you can use the Daily Build. Daily builds are available for all platforms.

## Source Code

The source code for QGroundControl is hosted on GitHub at [https://github.com/mavlink/qgroundcontrol](https://github.com/mavlink/qgroundcontrol). QGroundControl is dual-licensed under Apache 2.0 and GPLv3.

To obtain the source files, follow these steps:

1. Clone the repository (or your fork) including submodules:
   ```bash
   git clone --recursive -j8 https://github.com/mavlink/qgroundcontrol.git
   
Update submodules (required each time you pull new source code): git submodule update --recursive

Please note that GitHub source-code zip files cannot be used since they do not contain the appropriate submodule source code. You must use git for cloning.

Build QGroundControl
Using Containers
We support Linux builds using a container found in the source tree of the repository. This container facilitates the development and deployment of QGC apps without requiring you to install any of the necessary requirements on your local environment. For detailed instructions, refer to the Container Guide.

Native Builds
QGroundControl supports native builds on macOS, Linux, Windows, iOS, and Android. QGroundControl utilizes Qt as its cross-platform support library and QtCreator as its default build environment. Specific requirements for each platform are as follows:

macOS: v10.11 or higher
Ubuntu: 64 bit, gcc compiler
Windows: Vista or higher, Visual Studio 2019 compiler (64 bit)
iOS: 10.0 and higher
Android: Android 5.0 and later, standard QGC is built against NDK version 19, and Java JDK 11 is required.
Qt version: 5.15.2 (only) – Do not use any other version of Qt, as other versions may introduce stability and safety issues.
For more platform-specific information, refer to the Qt 5 supported platform list.

Install Visual Studio 2019 (Windows Only)
To build on Windows, you need to install the Visual Studio 2019 compiler. You can find it here. During installation, select "Desktop development with C++."

Install Qt
You need to install Qt as follows:

Download and run the Qt Online Installer.
On Ubuntu, make the downloaded file executable using: chmod +x.
Install Qt to the default location for use with ./qgroundcontrol-start.sh. If you install Qt to a non-default location, you will need to modify qgroundcontrol-start.sh.
In the installer, choose version 5.15.2, and install the required components based on your platform.
Install Additional Packages (Platform Specific)
Depending on your platform, you may need to install additional packages:

Ubuntu: sudo apt-get install speech-dispatcher libudev-dev libsdl2-dev patchelf build-essential curl
Fedora: sudo dnf install speech-dispatcher SDL2-devel SDL2 systemd-devel patchelf
Arch Linux: pacman -Sy speech-dispatcher patchelf
Android: Follow the Qt Android Setup and ensure you have JDK 11 installed.
Install Optional/OS-Specific Functionality
Optional features that depend on the operating system and user-installed libraries are linked/described in the documentation. You can forcibly enable/disable these features by specifying additional values to qmake.

For example, to disable the Airmap feature on Ubuntu, create a file named user_config.pri in the repository root directory containing the text DEFINES += DISABLE_AIRMAP. You can do this in a bash terminal using the following command: echo -e "DEFINES += DISABLE_AIRMAP\r\n" | tee user_config.pri
Building using Qt Creator
To build QGroundControl using Qt Creator, follow these steps:

Launch Qt Creator and open the qgroundcontrol.pro project.

In the Projects section, select the appropriate kit for your needs. Choose the kit that corresponds to your platform.

Build the project using the "hammer" or "play" icons in Qt Creator.

For iOS builds, use XCode as specified.

Congratulations! You have successfully set up and built QGroundControl.
