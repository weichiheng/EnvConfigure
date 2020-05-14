The code was tested on Ubuntu 18.04, with Anaconda Python3.6 and Pytorch v1.4.0. After install Anaconda:  
    1.create a new conda environment.  
    ```
    conda create --name CenterNet python=3.6  
    ```
    And activate the environment.  
    ```
    conda activate CenterNet  
    ```
    2.Install pytorch1.4.0  
    ```
    conda install pytorch=1.4 torchvision cudatoolkit=10.1 -c pytorch  
    ```
    If HTTP error, retry.  
    Then disable cudnn batch normalization.  
    ```
    gedit ~/anaconda3/envs/CenterNet/lib/python3.6/site-packages/torch/nn/functional.py  
    ```
    change the "torch.backends.cudnn.enabled" with "False" in line 1670.  
    3.Clone the Centernet project  
    ```
    cd /path/to/clone/CenterNet  
    git clone https://github.com/xingyizhou/CenterNet  
    ```
    4.Install COCOAPI  
    ```
    cd CenterNet  
    git clone https://github.com/cocodataset/cocoapi.git  
    cd cocoapi/PythonAPI/  
    pip install Cython  
    make  
    python setup.py install --user  
    ```
    5.Install the requirements  
    ```
    cd ..
    cd ..
    pip install -r requirements.txt
    ```
    6.Compile deformable convolutional 
    ```
    cd src/lib/models/networks
    rm -r DCNv2
    git clone https://github.com/CharlesShang/DCNv2.git
    cd DCNv2
    ./make.sh
    ```
    7.[Optional, only required if you are using extremenet or multi-scale testing] Compile NMS if your want to use multi-scale testing or test ExtremeNet.
    ```
    cd ..
    cd ..
    cd ..
    cd external/
    make
    ```   
    Congratulations! The environment configure has finished.
