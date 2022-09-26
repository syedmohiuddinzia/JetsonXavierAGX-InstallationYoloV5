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

Step 4. Edit the following lines. And then press ```Ctrl+S``` then ```Ctrl+X```to save and exit.
```bash
matplotlib==3.2.2
numpy==1.19.4
# torch>=1.7.0
# torchvision>=0.8.1
```
