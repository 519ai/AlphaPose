## Installation

### Requirements
* Python 3.5+
* Cython
* PyTorch 1.1+
* torchvision 0.3.0+
* Linux, [Windows user check here](#Windows)

### Code installation

#### (Recommended) Install with conda

Install conda from [here](https://repo.anaconda.com/miniconda/).
```shell
# 1. Create a conda virtual environment.
conda create -n alphapose python=3.6 -y
conda activate alphapose

# 2. Install PyTorch
conda install pytorch==1.1.0 torchvision==0.3.0

# 3. Get AlphaPose
git clone https://github.com/MVIG-SJTU/AlphaPose.git
cd AlphaPose

# 4. install
export PATH=/usr/local/cuda/bin/:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda/lib64/:$LD_LIBRARY_PATH
pip install cython
sudo apt-get install libyaml-dev
python setup.py build develop
```

#### Install with pip
```shell
# 1. Install PyTorch
pip3 install torch==1.1.0 torchvision==0.3.0

# 2. Get AlphaPose
git clone https://github.com/MVIG-SJTU/AlphaPose.git
cd AlphaPose

# 3. install
export PATH=/usr/local/cuda/bin/:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda/lib64/:$LD_LIBRARY_PATH
pip install cython
sudo apt-get install libyaml-dev
python setup.py build develop --user
```

#### Windows
For Windows user, if you meet error with PyYaml, you can download and install it manually from here: https://pyyaml.org/wiki/PyYAML.
If your OS platform is `Windows`, make sure that Windows C++ build tool like visual studio 15+ or visual c++ 2015+ is installed for training.

### Models
1. Download the object detection model manually: **yolov3-spp.weights**([Google Drive](https://drive.google.com/open?id=1D47msNOOiJKvPOXlnpyzdKA3k6E97NTC) | [Baidu pan](https://pan.baidu.com/s/1Zb2REEIk8tcahDa8KacPNA)). Place it into `detector/yolo/data`.

2. For pose tracking, download the object tracking model manually: **JDE-1088x608-uncertainty**([Google Drive](https://drive.google.com/open?id=1nlnuYfGNuHWZztQHXwVZSL_FvfE551pA) | [Baidu pan](https://pan.baidu.com/s/1Ifgn0Y_JZE65_qSrQM2l-Q)). Place it into `detector/tracker/data`.

2. Download our pose models. Place them into `pretrained_models`. All models and details are available in our [Model Zoo](./MODEL_ZOO.md).

### Prepare dataset (optional)

If you want to train the model by yourself, please download data from [MSCOCO](http://cocodataset.org/#download) (train2017 and val2017). Download and extract them under `./data`, and make them look like this:
```
|-- json
|-- exp
|-- alphapose
|-- configs
|-- test
|-- data
`-- |-- coco
    `-- |-- annotations
        |   |-- person_keypoints_train2017.json
        |   `-- person_keypoints_val2017.json
        |-- train2017
        |   |-- 000000000009.jpg
        |   |-- 000000000025.jpg
        |   |-- 000000000030.jpg
        |   |-- ... 
        `-- val2017
            |-- 000000000139.jpg
            |-- 000000000285.jpg
            |-- 000000000632.jpg
            |-- ... 
```
