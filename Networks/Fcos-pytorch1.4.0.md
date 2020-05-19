### 1.Clone the code from github.

```
git clone https://github.com/tianzhi0549/FCOS.git
```

### 2.Install

```
conda create --name FCOS python=3.7
conda activate FCOS
conda install ipython
pip install ninja yacs cython matplotlib tqdm
conda install pytorch=1.4.0 torchvision cudatoolkit=10.2 -c pytorch
pip install torchvision==0.5.0
cd FCOS
git clone https://github.com/cocodataset/cocoapi.git
cd cocoapi/PythonAPI
python setup.py build_ext install --user
cd ..
cd ..
python setup.py build develop --no-deps
```

### 3.onnx

Finished!
