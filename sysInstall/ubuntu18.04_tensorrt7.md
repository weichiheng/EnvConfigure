ubuntu18.04 with caffe，pytorch, tensorrt 7.0, onnx(latest).
1.Install the ubuntu18.04.(Close the secure boot)
2.Install the nvidia driver.
sudo apt-get update
sudo apt-get upgrade
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
ubuntu-drivers devices
sudo apt-get install nvidia-driver-440 #CUDA10.2
reboot
If no error is reported, the nvidia driver has been installed
using nvidia-smi check.
3.Install CUDA 10.2
cd /path/to/cuda.run/dir
sudo sh cuda_10.2.89_xxxxxx.run
4.Add environment variables
sudo getdit ~/.bashrc
export CUDA_HOME=/usr/local/cuda
export PATH=$PATH:$CUDA_HOME/bin
export LD_LIBRARY_PATH=/usr/local/cuda-10.2/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
source ~/.bashrc
Test the install of CUDA
cd /usr/local/cuda/samples/1_Utilities/deviceQuery 
sudo make
./deviceQuery
If Result = PASS, CUDA has been installed.
5.Install cuDNN
unzip the cudnn-xxx.tgz
cd cudnn-xxx/
sudo cp cuda/include/cudnn.h /usr/local/cuda/include/ 
sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64/ 
sudo chmod a+r /usr/local/cuda/include/cudnn.h 
sudo chmod a+r /usr/local/cuda/lib64/libcudnn*

use cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2 to check the version of cuDNN.
6.Install cmake
sudo apt-get install libssl-dev
Download the latest cmake website
ubzip cmake-xxx.tar.gz to your home dir.
cd cmake-xxx
sudo ./bootstrap
sudo make
sudo make install

7.Install Anaconda
sh ./Anaconda3-xxx.sh

8.Install OpenCV
Download the latest OpenCV source in OpenCV website.
unzip opencv-xxx.zip to your home dir.
cd opencv-xxx
mkdir build
cd build
sudo cmake ..
sudo make -j64
sudo make install

9.Configure caffe
sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler
sudo apt-get install --no-install-recommends libboost-all-dev
sudo apt-get install libopenblas-dev liblapack-dev libatlas-base-dev
sudo apt-get install libgflags-dev libgoogle-glog-dev liblmdb-dev
sudo apt-get install git build-essential
sudo apt-get install python-numpy
sudo apt-get install python-skimage
sudo apt-get install python-protobuf
If /sbin/ldconfig.real: /usr/local/cuda-10.2/targets/x86_64-linux/lib/libcudnn.so.7 is not a symbolic link
sudo ln -sf /usr/local/cuda-10.2/targets/x86_64-linux/lib/libcudnn.so.7.6.5 /usr/local/cuda-10.2/targets/x86_64-linux/lib/libcudnn.so.7
mkdir build
cd build
sudo cmake ..
sudo make -j64
sudo make pycaffe
sudo make install #Optional
cd ..
cd pyton
sudo python
import caffe
sudo gedit ~/.bashrc
export PYTHONPATH=/path/to/caffe/python:$PYTHONPATH
source ~/.bashrc






