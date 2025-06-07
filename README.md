# 723_cruise_control
A Cruise Control system implemented in Esterel, compiled to C, and executed using the XES simulator. Designed for educational use, this project includes modular state management and simulation of vehicle control logic.

📋 Prerequisites
Recommended Tools (for VSCode)
Install the following extensions to improve your development experience:

C/C++ extension (ms-vscode.cpptools)

Kieler extension (kieler.keith-vscode) for SCCharts visualisation

🛠️ Setup Instructions
🔧 Option 1: Using FlexIT (University of Auckland VM)
Access the Ubuntu virtual machine via FlexIT

Add the Esterel compiler to your PATH by running the following command:

export PATH=$PATH:/opt/esterelv6_01/bin

Note: Avoid compiling from a mounted virtual disk such as tsclient. Instead, copy your project files to the VM's local disk for stable compilation.

💻 Option 2: Local Installation (Without FlexIT)
Check if Esterel tools are available:

esterel -version

xes -version

xeve -version

If commands are not recognized, but Esterel is installed, you may need to manually link executables:

Example: Create a symbolic link to xeve

sudo ln -s /path_to/esterel_distro/bin/xeve /usr/local/bin/xeve

Check the link: ls -l /usr/local/bin/xeve

Update the Makefile:

Change line 31 to point to your local Esterel installation

export ESTEREL = /path_to/esterel_distro

Install required dependencies (on Ubuntu):

Run: sudo apt update

Install 32-bit GCC support: sudo apt install gcc-multilib

Install 32-bit development headers: sudo apt install libc6-dev-i386

Install 32-bit X11 development libraries: sudo apt install libx11-dev:i386

▶️ Running the Simulator
Navigate to the src directory:

cd src

Compile the simulation binary:

make cruisecontrol.xes

Execute the simulator:

./cruisecontrol.xes


⌨️ Inputs
Name	Type	Description
On	boolean	Enables the cruise control system
Off	boolean	Turns the cruise control system off
Resume	boolean	Resumes the last stored cruise speed
Set	boolean	Stores current speed as the cruise speed
QuickDecel	boolean	Decreases cruise speed by a fixed amount
QuickAccel	boolean	Increases cruise speed by a fixed amount
Accel	float	Driver's accelerator input
Brake	float	Driver's brake input
Speed	float	The current speed of the vehicle

📤 Outputs
Name	Type	Description
CruiseSpeed	float	The target speed maintained by the cruise system
ThrottleCmd	float	The throttle signal to be sent to the car's engine system
CruiseState	integer	Integer code representing the cruise control state
