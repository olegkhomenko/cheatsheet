### TensorFlow
__Check for available GPUs__

```python
from tensorflow.python.client import device_lib

def get_available_gpus():
     local_device_protos = device_lib.list_local_devices()
     return [x.name for x in local_device_protos if x.device_type == 'GPU']
```

__Export ENVs__
export CUDA_HOME=/usr/local/cuda
export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/cuda/lib64:/usr/local/cuda/extras/CUPTI/lib64"
