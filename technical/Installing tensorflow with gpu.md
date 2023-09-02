# Installing tensorflow with gpu
Linux:
1. Ensure that you have nvidia drivers installed: (if not, then do the following)
```bash
apt search nvidia-driver
sudo apt install libnvidia-common-535
sudo apt-get -y install libnvidia-gl-535
sudo apt install nvidia-driver-535-server
sudo reboot
```
- Make sure to replace all instances of “535” with the version of nvidia driver you want to use

2. Install cuda on ubuntu and double check that your driver recognizes your gpu:
```bash
sudo apt install nvidia-cuda-toolkit
nvidia-smi
```

3. Activate your conda environment that you want to use tensorflow in and run the following commands:
```bash
conda install -c conda-forge cudatoolkit=11.8.0
python3 -m pip install nvidia-cudnn-cu11==8.6.0.163 tensorflow==2.13.*
mkdir -p $CONDA_PREFIX/etc/conda/activate.d
echo 'CUDNN_PATH=$(dirname $(python -c "import nvidia.cudnn;print(nvidia.cudnn.__file__)"))' >> $CONDA_PREFIX/etc/conda/activate.d/env_vars.sh
echo 'export LD_LIBRARY_PATH=$CONDA_PREFIX/lib/:$CUDNN_PATH/lib:$LD_LIBRARY_PATH' >> $CONDA_PREFIX/etc/conda/activate.d/env_vars.sh
source $CONDA_PREFIX/etc/conda/activate.d/env_vars.sh
# Verify install:
python3 -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"
```

## Possible bugs
Importing libraries → missing library “chardet”

```bash
pip install chardet
pip install --force-reinstall charset-normalizer==3.1.0
```

W tensorflow/compiler/xla/service/gpu/llvm_gpu_backend/gpu_backend_lib.cc:530] Can't find libdevice directory ${CUDA_DIR}/nvvm/libdevice. This may result in compilation or runtime failures, if the program we try to run uses routines from libdevice.

```bash
conda install -c nvidia cuda-nvcc=11.3.58
# Configure the XLA cuda directory
mkdir -p $CONDA_PREFIX/etc/conda/activate.d
printf 'export XLA_FLAGS=--xla_gpu_cuda_data_dir=$CONDA_PREFIX/lib/\n' >> $CONDA_PREFIX/etc/conda/activate.d/env_vars.sh 
source $CONDA_PREFIX/etc/conda/activate.d/env_vars.sh
# Copy libdevice file to the required path
mkdir -p $CONDA_PREFIX/lib/nvvm/libdevice
cp $CONDA_PREFIX/lib/libdevice.10.bc $CONDA_PREFIX/lib/nvvm/libdevice/
```
