# FLIP

**!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!**

**Notes**: FLIP is still under internal development and testing. Codes will be made public in this github repo later (est. summer of 2024) 

**!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!**

A <ins>F</ins>orest <ins>L</ins>idar <ins>I</ins>ntegrated toolset based on <ins>P</ins>ython

Authors: Xiangtao Xu, Tao Han, et al.

A formal and detailed description of `FLIP` package can be found in **TBD**

# Introduction
## Why FLIP ?
Recent years, terrestrial laser scanning (TLS) sees many applications in forestry as TLS can measure the forest structure with high spatial detail and accuracy. However, the diffculty to access the information content of point clouds limit the utilization of TLS. To obtain tree-scale metrics (DBH, basel area, volume, etc...), we must segment individual trees from forest-level point clouds. This process often means intensive manual segmentation, which is a impossible task where hundreds of trees or large forest area exists.

Here, `FLIP` is an open-source python-based integrated tool, which can support rapid tree segmentation (1 to 4 hours depends on your computation power) from LiDAR point clouds of different forest biomes (temporal, tropical and boreal). The `FLIP` package provides functions for i) data preprocessing (point clouds cropping, subsampling and filtering), ii) ground layer and above ground height extraction, iii) extract and assemble linear units from point clouds, and many more functions in the future!

## Installation

To implement this toolbox you need to install the required Python packages in an environment. You will need a recent installation of [Anaconda3](https://www.anaconda.com/) or [miniconda3](https://docs.conda.io/en/latest/miniconda.html). Once you installed Anaconda or miniconda on your PC, open the Anaconda prompt and change current directory to locate the folder where you downloaded `FLIP` package. Then, create a new environment named `CloudCompy39` (you can set any name you want) and install all the required packages.

### Required packages
* [CloudCompy](https://github.com/CloudCompare/CloudComPy)
* anytree
* hdbscan
* scikit-learn

Now, all the required packages have been installed in an environment named `CloudCompy39`. Make sure activate the environment before running `FLIP` repository:

```python
# activate the environment
conda activate CloudCompy39
# rem this script sets the environment for CloudComPy. The Conda environment must be activated before calling this script.
envCloudCompy.bat 
```

# Getting Started
## Preprocessing
### Point clouds cropping

```python

# create boundary box according to the coordinates of scanpositions 
# INPUT_DIR should include "ScanPosition.txt"

```

### Downsampling and filtering
```python

# subsample point clouds within the box (default value of 0.03 m)
SubSampleCloud_MP()

# filter point clouds
pc_filter = FilterCloud()
```
See more details in [config.yaml](https://github.com/than2/PITFli/blob/main/config.yaml) to get the default values of parameters used in functions.

### Get ground layer and above ground height
```python
cloud_ground = GetGroundCloud(pc_filter)
cc.SavePointCloud(cloud_ground, GROUND_FILENAME)
pc_agh = GetAboveGroundHeight(pc_filter,cloud_ground)
cc.SavePointCloud(pc_agh, AGH_FILENAME)
```
add figures

## Segmentation
### Clustering
```python

# obtain all potential linear untis from cloud
N_stems = GetGeometricUnits(AGH_FILENAME, res= SEG_RES)
```

### Post-segmentation processing
```python
# add raw cloud and aggregate all trees
AssimilateRawCloud()
AggregateTrees()
```
add figures


# Contribution
Feedback and bug reports are welcome. Please write us at xiangtao@email.com if you want to make contributions.

# How to cite

Please cite us using the reference below if you use these codes in your research.

```python

@article{makecite,
  author       = {Xiangtao Xu},
  title        = {},
  journal      = {},
  year         = {},
  volume       = {},
  pages        = {}
  doi          = {}
}

```
