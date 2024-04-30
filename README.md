# MobileNet DPU Accelerated Inference System
This is a course project for UT Austin EE382N-4 Advanced Embedded Systems, Spring 2024.
We developed an example system for running DPU accelerated inference on the Ultra96 platform using AMD Pynq and Xilinx Vitis AI. The application is running a pose estimation model.

# Setup Instructions
In order to set this project up you will require the following
* An Ultra96-V2 SoC
* A micro-SD card
* USB cable for connecting the Ultra96 to your PC.
* Windows or Mac PC are easiest, Linux support is limited
* Balena Etcher software or similar for writing SD card image to disk
* USB2.0 to Ethernet adapter
* Mini DisplayPort to DisplayPort adapter
* USB2.0 webcam. 

## Step 1: Prepare the Ultra96 hardware.
Connect the Ultra96 to external power. Connect the Ultra96 to wired ethernet via the USB adapter. Connect your webcam to the Ultra96.
Connect the Ultra96 to a compatible monitor via DisplayPort. *Note: HDMI is not supported and a DisplayPort to HDMI adapter will not work*. 
Ensure the Ultra96 is powered off before inserting or removing the SD card.

## Step 2: Obtain board image and flash SD card
Download the Avnet Ultra96-V2 Pynq SD card image here: https://bit.ly/ultra96v2_v3_0_1
Insert the SD card into your PC and flash the board image using Balena Etcher or similar software.
Once that is finished, eject the SD card and insert it into the Ultra96-V2. Power on the Ultra96-V2

## Step 3: Connect to the Pynq operating system
There are a few ways to connect to Pynq.
The default username and password on this system are `xilinx`:`xilinx`.
### Windows and Mac
Connect a USB cable to your PC and the Ultra96 micro-USB port. Windows will recognize the connected device as an ethernet adapter as well as a network storage device.
You can connect to the Jupyter Notebook environment running on the Ultra96 from your PC or Mac by navigating to `192.168.3.1`. You can transfer files to-from the Ultra96 via the network storage device.
### Linux
When tested on my system, there was no support for connecting the device as an ethernet adapter or network storage device. 
However, if you know the local IP address of the Ultra96 you can ssh to it directly, using the default username and password.
The system will have a dynamically assigned IP, and is also available via hosname `pynq`. E.g. `ssh xilinx@pynq.lan`.
You can also connect to Jupyter Notebook by navigating your browser to `http://pynq.lan:9090`.
When connecting via SSH, the USB cable connection to the PC is not required.

## Step 4: Prepare the project environment
### Windows and Mac
Clone this repo to your local machine and copy all files over to the Pynq network storage.
### Linux
Clone the repo directly on the board or copy it from your local host.

## Step 5: Run the demo
In Jupyter, navigate to the demo notebook and simply execute the cells in order to prepare the model and run inference.
