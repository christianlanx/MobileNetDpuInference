# MobileNet DPU Accelerated Inference System
This is a course project for UT Austin EE382N-4 Advanced Embedded Systems, Spring 2024.
We developed a system for running DPU accelerated inference on the Ultra96V2 platform using AMD Pynq [2] and Xilinx Vitis AI [1]. The application is running a pose estimation model using MobileNetV2 [6] as the backbone. The pose estimation model was trained using a single A100 GPU and the MPII Human Pose Database [4]. The training code and portions of the code used for inference were obtained from the MobilePose GitHub repository [5]. To integrate the DPU with the PYNQ ecosystem, we use the PYNQ DPU overlay [3].

# Setup Instructions
In order to set this project up you will require the following:
* Ultra96-V2 SoC
* Micro-SD card
* Micro-USB to USB cable for connecting the Ultra96V2 to a PC
* Windows or Mac PC are easiest, Linux support is limited
* Balena Etcher software or similar for writing the SD card image to disk
* USB2.0 to Ethernet adapter for Python library installations
* Mini DisplayPort to DisplayPort adapter
* USB2.0 webcam

## Step 1: Obtaining and Flashing the Board Image
1. Download the Avnet Ultra96-V2 Pynq SD card image here: https://bit.ly/ultra96v2_v3_0_1.
2. Insert the SD card into your PC and flash the board image using Balena Etcher or similar software.
3. Once that is finished, eject the SD card and insert it into the Ultra96-V2.

## Step 2: Preparing the Ultra96 Hardware
1. Connect the Ultra96 to external power. 
2. Connect the Ultra96 to wired ethernet via the USB adapter. 
3. Connect your webcam to the Ultra96.
4. Connect the Ultra96 to a compatible monitor via DisplayPort. *Note: HDMI is not supported and a DisplayPort to HDMI adapter will not work*. 
5. Ensure the Ultra96 is powered off before inserting or removing the SD card.

## Step 3: Connecting to the PYNQ Jupyter Notebook Environment
There are a few ways to connect to Pynq.
The default username and password on this system are `xilinx`:`xilinx`.
### Windows and Mac
1. Connect a USB cable to your PC and the Ultra96 micro-USB port. Windows will recognize the connected device as an ethernet adapter as well as a network storage device.
2. You can connect to the Jupyter Notebook environment running on the Ultra96 from your PC or Mac by navigating to `192.168.3.1:9090`. You can transfer files to-from the Ultra96 via the network storage device.
### Linux
1. When tested on my system, there was no support for connecting the device as an ethernet adapter or network storage device. However, if you know the local IP address of the Ultra96 you can ssh to it directly, using the default username and password.
2. The system will have a dynamically assigned IP, and is also available via hostname `pynq`. E.g. `ssh xilinx@pynq.lan`.
3. You can also connect to Jupyter Notebook by navigating your browser to `http://pynq.lan:9090`.
When connecting via SSH, the USB cable connection to the PC is not required.

## Step 4: Preparing the Project Environment
### Windows and Mac
1. Clone this repository to your local machine and copy all files over to the PYNQ network storage.
### Linux
1. Clone the repositroy directly on the board or copy it from your local host. Make sure to clone the repository into the Jupyter Notebook home folder `cd $PYNQ_JUPYTER_NOTEBOOKS`.

## Step 5: Running the Demo
1. Install the required Python libraries by opening a terminal in Jupyter. Use the following commands `pip install -r requirements.txt` and `pip install pynq-dpu --no-build-isolation`. Note, this will not work without an internet connection.
1. In Jupyter, navigate to the demo notebook and simply execute the cells in order to prepare the model and run inference.

## References
[1] Vitis AI: https://www.xilinx.com/products/design-tools/vitis/vitis-ai.html

[2] AMD PYNQ: https://www.pynq.io/

[3] DPU-PYNQ: https://github.com/Xilinx/DPU-PYNQ

[4] MPII Human Pose Database: http://human-pose.mpi-inf.mpg.de/

[5] MobilePose: https://github.com/YuliangXiu/MobilePose

[6] MobileNetV2: https://arxiv.org/abs/1801.04381
