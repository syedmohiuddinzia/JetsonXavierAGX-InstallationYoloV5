# JetsonXavierAGX - YoloV5 Installation
In this repository the installation procedure of YoloV5 is discussed.

## Prerequisites
First of all check if latest JetPack v4.6.1 with all SDK components installed. This can be checked by the following command.
```
 jetson_release -v
 ```
 If latest JetPack v4.6.1 with all SDK components is not installed, then install it first. The second method is to check using the the __jtop Package__.

### jtop Package (Advance)
__jtop__ is a simple package to monitoring and control your NVIDIA Jetson. We can use the jtop tool to check the version number of the SDK components installed by Jetson or the working status of the whole machine. </br>

The jtop tool relies on the pip tool, so we need to install pip on your Jetson first.
```
sudo apt install python3-pip
```
Then we can download jtop directly through the pip tool. </br>

```
sudo -H pip3 install -U jetson-stats
```

![1](https://github.com/syedmohiuddinzia/JetsonXavierAGX-InstallationYoloV5/blob/main/1.png)
 </br>
Type ```jtop``` directly into the command line, and a pop-up window will dynamically display the current work of Jetson. </br>
 </br>
![2](https://github.com/syedmohiuddinzia/JetsonXavierAGX-InstallationYoloV5/blob/main/2.png)
 </br>
By pressing the number key 6, you can see the Jetson's jetpack version and even information about the SDK component directly in the window.
</br>
![3](https://github.com/syedmohiuddinzia/JetsonXavierAGX-InstallationYoloV5/blob/main/3.png)
