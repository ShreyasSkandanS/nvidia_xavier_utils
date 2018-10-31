# Pytorch Installation on Jetson Xavier

## 1. Install PyTorch and test code

Get the Pytorch pip wheels released by NVIDIA:
Python3.6: https://drive.google.com/file/d/1h3nsVXskS8yQvLmhrL77m8mImusRy7OR/view
Python2.7: https://drive.google.com/file/d/12ywd_wzkPAfsZIv8pP7lPb7YBSpzM44x/view

For **Python3.6**
```
sudo apt-get install python3-pip
pip3 install torch-1.0.0a0+8601b33-cp36-cp36m-linux_aarch64.whl
pip3 install numpy
```

If you're using **Python2.7**
```
sudo apt-get install python-pip
pip install torch-1.0.0a0+8601b33-cp27-cp27mu-linux_aarch64.whl
pip install numpy
```

The following commands can be run using pip or pip3 depending your preferred
python version

#### b) Additional packages

You will most likely need Torch Vision and the necessary dependencies

```
pip3 install torchvision --no-deps
```
and Scikit-image
```
sudo apt-get install gfortran
```

```
pip3 install Cython
pip3 install scikit-image
```

#### c) Download SS_Segmentation package

```
git clone https://github.com/ShreyasSkandanS/ss_segmentation.git
```

Follow setup instructions (for testing/inference).

On our data/model we noticed a 1.8X increase without any Xavier specific
optimizations. No NVDLA cores were used.

#### d) Benchmark

![GrayImage](/figs/gray_image.gif)
![Output](/figs/semseg_inf.gif)
![SemSegBenchmark](/figs/semseg.png)

## 2. Loading Multi-GPU Trained Models

If you've trained a network on a multi-gpu setup and naively exported the model
to a *model.pth.tar* format, you're likely to see something like this show up as
an error:

```
torch.cuda.nccl.NcclError: System Error (2)
```

For the same reasons mentioned
[here](https://shreyasskandan.github.io/posts/pytorch_notes/), load your model
and remove all bindings to the *DataParallel* class and you should be able
successfully run your code,

```
pretrained_model = checkpoint['model']
new_model = SomeNetwork()
from collections import OrderedDict
new_model_dict = OrderedDict()
for k,v in pretrained_model.state_dict().items():
    # Drop the "Module." characters from the name
    name = k[7:]
    new_model_dict[name] = v
new_model.load_state_dict(new_model_dict)
```

## 3. ONNX and PyTorch


#### a) Export PyTorch Model to ONNX

Based on
[this](https://github.com/onnx/tutorials/blob/master/tutorials/PytorchOnnxExport.ipynb)
tutorial.

Install Protobuf compiler
```
sudo apt-get install protobuf-compiler libprotoc-dev
```

Install ONNX
```
pip3 install onnx
```

Check if your install is working
```
python3 -c "import onnx"
```

For PyTorch, it appears there's official support for ONNX in the form of a
torch.onnx library. Check to see if your version of PyTorch contains this
library:
```
import torch.onnx
```

Exporting your PyTorch model to ONNX is then a matter of calling the
*torch.onnx.export* function. You can find more details aout this method here;

```
import torch.onnx
help(torch.onnx.export)
```


