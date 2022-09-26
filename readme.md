# JetsonXavierAGX - YoloV5 Installation
In this repository the installation procedure of YoloV5 is discussed.

## Prerequisites
First of all check if latest JetPack v4.6.1 with all SDK components installed. This can be checked by the following procedure. </br>

### jtop Package
__jtop__ is a simple package to monitoring and control your NVIDIA Jetson. We can use the jtop tool to check the version number of the SDK components installed by Jetson or the working status of the whole machine. </br>

The jtop tool relies on the pip tool, so we need to install pip on your Jetson first.
```
sudo apt install python3-pip
```
Then we can download jtop directly through the pip tool.

```
sudo -H pip3 install -U jetson-stats
```
