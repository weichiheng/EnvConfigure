<p>The code was tested on Ubuntu 18.04, with Anaconda Python3.6 and Pytorch v1.4.0. After installing Anaconda:  </p>
<h3>1.create a new conda environment.  </h3>
<pre><code>conda create --name CenterNet python=3.6  
</code></pre>
<p>    And activate the environment.  </p>
<pre><code>conda activate CenterNet
</code></pre>
<h3>2.Install pytorch1.4.0  </h3>
<pre><code>conda install pytorch=1.4 torchvision cudatoolkit=10.1 -c pytorch  
</code></pre>
<p>    If HTTP error, retry.<br/>    Then disable cudnn batch normalization.  </p>
<pre><code>gedit ~/anaconda3/envs/CenterNet/lib/python3.6/site-packages/torch/nn/functional.py  
</code></pre>
<p>    change the <code>torch.backends.cudnn.enabled</code> with <code>False</code> in line 1670.  </p>
<h3>3.Clone the Centernet project  </h3>
<pre><code>cd /path/to/clone/CenterNet  
git clone https://github.com/xingyizhou/CenterNet  
</code></pre>
<h3>4.Install COCOAPI  </h3>
<pre><code>cd CenterNet  
git clone https://github.com/cocodataset/cocoapi.git  
cd cocoapi/PythonAPI/  
pip install Cython  
make  
python setup.py install --user  
</code></pre>
<h3>5.Install the requirements  </h3>
<pre><code>cd ..
cd ..
pip install -r requirements.txt
</code></pre>
<h3>6.Compile deformable convolutional  </h3>
<pre><code>cd src/lib/models/networks
rm -r DCNv2
git clone https://github.com/CharlesShang/DCNv2.git
cd DCNv2
./make.sh
</code></pre>
<h3>7.Compile NMS if your want to use multi-scale testing or test ExtremeNet.  </h3>
<p>[Optional, only required if you are using extremenet or multi-scale testing] </p>
<pre><code>cd ..
cd ..
cd ..
cd external/
make
</code></pre>
<p>
Congratulations! The environment configure has finished.</p>
