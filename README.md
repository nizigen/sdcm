<h1 align="center"> SD Cross-View Matching System based on University-1652 </h1>


##### This system implements a cross-view image retrieval and matching task based on the University-1652 dataset, with a primary focus on matching drone images with satellite images.

**Task 1: Drone-view target localization.** (Drone -> Satellite) Given one drone-view image , Return the top five most similar satellite images ranked by similarity score.

**Task 2: Drone navigation.** (Satellite -> Drone) Given one satellite-view image, Return the top five most similar satellite images ranked by similarity score.

</details>

## Table of contents

* [About Dataset](#about-dataset)
* [Prerequisites](#prerequisites)
* [Getting Started](#getting-started)
  * [Installation](#installation)
  * [Dataset Preparation](#dataset--preparation)
  * [Train Evaluation ](#train--evaluation)
  * [Trained Model and Feature dataset](#trained--model)

## About Dataset

The dataset split is as follows: 

| Split             | #imgs  | #buildings | #universities |
| ----------------- | ------ | ---------- | ------------- |
| Training          | 50,218 | 701        | 33            |
| Query_drone       | 37,855 | 701        | 39            |
| Query_satellite   | 701    | 701        | 39            |
| Query_ground      | 2,579  | 701        | 39            |
| Gallery_drone     | 51,355 | 951        | 39            |
| Gallery_satellite | 951    | 951        | 39            |
| Gallery_ground    | 2,921  | 793        | 39            |

More detailed file structure:

```
├── University-1652/
│   ├── readme.txt
│   ├── train/
│       ├── drone/                   /* drone-view training images 
│           ├── 0001
|           ├── 0002
|           ...
│       ├── street/                  /* street-view training images 
│       ├── satellite/               /* satellite-view training images       
│       ├── google/                  /* noisy street-view training images (collected from Google Image)
│   ├── test/
│       ├── query_drone/  
│       ├── gallery_drone/  
│       ├── query_street/  
│       ├── gallery_street/ 
│       ├── query_satellite/  
│       ├── gallery_satellite/ 
│       ├── 4K_drone/
```

## Prerequisites

- Python 3.6+
- GPU Memory >= 8G
- Numpy > 1.12.1
- Pytorch 0.3+ 
- [Optional] apex (for float16) 

## Getting started

### Installation

First, create a virtual environment (e.g., named modnet) with Python (3.6+) using your favourite environment manager (the following instructions use [conda](https://docs.conda.io/)):

```bash
conda create -n sd python=3.9
```

Activate the environment:

```bash
conda activate sd
```

Install this system by：

```bash

```

Install Pytorch from http://pytorch.org/

Install required packages

```bash
cd sdcm
pip install -r requirement.txt
```

Dataset & Preparation：

Download [University-1652]  form this [link](https://drive.usercontent.google.com/download?id=1iVnP4gjw-iHXa0KerZQ1IfIO0i1jADsR).

After download, please put change the dataset folder under the program and change its name to data .Set the structure like `./data/`.

## Train & Evaluation 

### Train & Evaluation sdcm

```
python train.py --name three_view_long_share_d0.75_256_s1_google  --extra --views 3  --droprate 0.75  --share  --stride 1 --h 256  --w 256 --fp16; 
python test.py --name three_view_long_share_d0.75_256_s1_google
```

### Show the retrieved Top-5 results 

```
python test.py --name three_view_long_share_d0.75_256_s1_google # after test
python demo.py --query_index 0 # which image you want to query in the query set 
```

It will save an image named `show.png' containig top-5 retrieval results in the folder. 

## Trained Model and Feature dataset

You could download the trained model and Feature dataset at [Baidu Netdisk]( https://pan.baidu.com/s/14s4Tz2FRXChaCdV6t9jbgQ?pwd=vrjz) .After download, please put model folders under `./model/`.
