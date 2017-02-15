### TensorFlow
__Check for available GPUs__

```python
from tensorflow.python.client import device_lib

def get_available_gpus():
     local_device_protos = device_lib.list_local_devices()
     return [x.name for x in local_device_protos if x.device_type == 'GPU']
```

__Export ENVs__
```bash
export CUDA_HOME=/usr/local/cuda
export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/cuda/lib64:/usr/local/cuda/extras/CUPTI/lib64"
```

__Status in shell for NVIDIA GPUs__
```bash
nvidia-smi -l 1
```

__Save & Load ```model```__

_Save_
```python
# serialize model to JSON
model_json = model.to_json()
with open("model.json", "w") as json_file:
    json_file.write(model_json)
# serialize weights to HDF5
model.save_weights("model.h5")
print("Saved model to disk")
```
_Load_
```python
# load json and create model
json_file = open('model.json', 'r')
loaded_model_json = json_file.read()
json_file.close()
loaded_model = model_from_json(loaded_model_json)
# load weights into new model
loaded_model.load_weights("model.h5")
print("Loaded model from disk")
```
