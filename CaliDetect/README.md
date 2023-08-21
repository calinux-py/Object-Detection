# GStreamer camera examples with Coral (CaliNux Version)

This folder contains example code using [GStreamer](https://github.com/GStreamer/gstreamer) to
obtain camera images and perform image classification and object detection on the Edge TPU.

This code works on Linux using a webcam, Raspberry Pi with the Pi Camera, and on the Coral Dev
Board using the Coral Camera or a webcam. For the first two, you also need a Coral
USB/PCIe/M.2 Accelerator.


## Set up your device

1.  First, be sure you have completed the [setup instructions for your Coral
    device](https://coral.ai/docs/setup/). If it's been a while, repeat to be sure
    you have the latest software.

    Importantly, you should have the latest TensorFlow Lite runtime installed
    (as per the [Python quickstart](
    https://www.tensorflow.org/lite/guide/python)). You can check which version is installed
    using the ```pip3 show tflite_runtime``` command.

2.  After downloading the CaliDetect repo, run these commands:

    ```
    echo "deb https://packages.cloud.google.com/apt coral-edgetpu-stable main" | sudo tee /etc/apt/sources.list.d/coral-edgetpu.list > /dev/null
    curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
    
    sudo apt-get update
    sudo apt-get install -y libedgetpu1-max python3-pycoral
    
    cd Object-Detection/CaliDetect
    chmod +x install_requirements.sh
    ./install_requirements.sh
    ```

3.  Change path for default_model_dir by editing detect.py:

    By default, the script will not work until you change the path to your username directory.

4.  Run detection:

    ```
    python detect.py
    ```

By default, both examples use the attached Coral Camera. If you want to use a USB camera,
edit the ```gstreamer.py``` file and change ```device=/dev/video0``` to ```device=/dev/video1```.


All rights to Google and Coral.AI.
I love your products.

