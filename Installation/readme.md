# Jetson Xavier AGX - YoloV5 Installation

This procedure is for Jetson device to perform inference on images with the help of the model generated from after training.

### Step 1. Access the terminal of Jetson device, install pip and upgrade it
```bash
sudo apt update
```
```bash
sudo apt install -y python3-pip
```
```bash
pip3 install --upgrade pip
```

### Step 2. Clone the following repo
```
git clone https://github.com/ultralytics/yolov5
```

### Step 3. Open requirements.txt
```bash
cd yolov5
sudo nano requirements.txt
```

### Step 4. Edit the following lines. And then press ```Ctrl+S``` then ```Ctrl+X```to save and exit.
```bash
matplotlib==3.2.2 # change the version
numpy==1.19.4 # change the version
# torch>=1.7.0 # hide this line
# torchvision>=0.8.1 # hide this line
```
___NOTE:___ _We include fixed versions for matplotlib and numpy to make sure there are no errors when running YOLOv5 later. Also, torch and torchvision are excluded for now because they will be installed later._

### Step 5. install the below dependency
```
sudo apt install -y libfreetype6-dev
```

### Step 6. Install the necessary packages
```
pip3 install -r requirements.txt
```

### Step 7. Install torch
```
cd ~
sudo apt-get install -y libopenblas-base libopenmpi-dev
wget https://nvidia.box.com/shared/static/fjtbno0vpo676a25cgvuqc1wty0fkkg6.whl -O torch-1.10.0-cp36-cp36m-linux_aarch64.whl
pip3 install torch-1.10.0-cp36-cp36m-linux_aarch64.whl
```

### Step 8. Install torchvision
```
sudo apt install -y libjpeg-dev zlib1g-dev
git clone --branch v0.9.0 https://github.com/pytorch/vision torchvision
cd torchvision
sudo python3 setup.py install 
```
## For using TensorRT engine (Advance)

NVIDIA® TensorRT™, is an SDK for high-performance deep learning inference, includes a deep learning inference optimizer and runtime that delivers low latency and high throughput for inference applications.
![1](https://github.com/syedmohiuddinzia/JetsonXavierAGX-InstallationYoloV5/blob/main/Installation/1.svg)
![2](https://github.com/syedmohiuddinzia/JetsonXavierAGX-InstallationYoloV5/blob/main/Installation/2.png)

### Step 9. Clone the following repo
```
cd ~
git clone https://github.com/wang-xinyu/tensorrtx
```
### Step 10. Copy roadsign-yolov5n.pt file we downloaded from previous training into yolov5 directory

### Step 11. Copy gen_wts.py from tensorrtx/yolov5 into yolov5 directory
```
cp tensorrtx/yolov5/gen_wts.py yolov5
```
### Step 12. Generate .wts file from PyTorch with .pt
```
cd yolov5
python3 gen_wts.py -w roadsign-yolov5n.pt
```
The above will generate roadsign-yolov5n.wts
### Step 13. Navigate to tensorrtx/yolov5
```
cd ~
cd tensorrtx/yolov5
```
### Step 14. Open yololayer.h with vi text editor
```
nano yololayer.h
```
### Step 15. Change CLASS_NUM to the number of classes your model is trained.
### Step 16. Create a new build directory and navigate inside
```
mkdir build 
cd build
```

Step 17. Copy the previously generated roadsign-yolov5n.wts file into this build directory
```
cp ~/yolov5/roadsign-yolov5n.wts .
```

Step 18. Compile it
```
cmake ..
make
```

Step 19. Serialize the model
```
sudo ./yolov5 -s [.wts] [.engine] [n/s/m/l/x/n6/s6/m6/l6/x6 or c/c6 gd gw]
#example
sudo ./yolov5 -s roadsign-yolov5n.wts roadsign-yolov5n.engine n
```
Here we use n because that is recommended for edge devices such as the NVIDIA Jetson platform.

```
sudo ./yolov5 -d roadsign-yolov5n.engine images
```
