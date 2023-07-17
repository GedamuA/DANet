##  DANet: Dual-attention Network for View-invariant Action  recognition.  

#we propose a Dual-Attention Network (DANet) aims to learn robust video representation for view-invariant action recognition. 
The DANet is composed of relation-aware spatiotemporal self-attention and spatiotemporal cross-attention modules.
The relation-aware spatiotemporal self-attention module learns representative and discriminative action features. This module
captures local and global long-range dependencies, as well as pairwise relations among human body parts and joints in the
spatial and temporal domains. The cross-attention module learns view-invariant attention maps and generates discriminative
features for semantic representations of actions in different views.


$$ Datasets

There are 3 datasets to download:

- NTU RGB+D 60 Skeleton
- NTU RGB+D 120 Skeleton
- UESTC skeleton Datatset

NTU RGB+D 60 and 120 Dataset
Request dataset here: http://rose1.ntu.edu.sg/Datasets/actionRecognition.asp
Download the skeleton datasets:
- nturgbd_skeletons_s001_to_s017.zip (NTU RGB+D 60)
- nturgbd_skeletons_s018_to_s032.zip (NTU RGB+D 120)
- Extract above files to ./data/nturgbd_raw
- 
UESTC Dataset
Request dataset here:  https://github.com/HRI-UESTC/CFM-HRI-RGB-D-action-database

## Dataset Preparation.  
Put downloaded data into the following directory structure:

- data/
  - UESTC/
      ... # raw data of UESTC
  - ntu/
  - ntu120/
  - nturgbd_raw/
    - nturgb+d_skeletons/     # from `nturgbd_skeletons_s001_to_s017.zip`
      ...
    - nturgb+d_skeletons120/  # from `nturgbd_skeletons_s018_to_s032.zip`
 
Generating Data:
```
cd ./data/ntu # or cd ./data/ntu120
 # Get skeleton of each performer
 python get_raw_skes_data.py
 # Remove the bad skeleton 
 python get_raw_denoised_data.py
 # Transform the skeleton to the center of the first frame
 python seq_transformation.py
```

## Attention Results
Here we present the attention results learned by DANet on the NTU-60 dataset, where the ellipses' radius are proportional to the joint relevance. The greenlight ellipses indicate the correct attention weights, with a larger radius corresponding to higher weights.

- DANet Attention weights (camera 1 (45 degree view).
![image](https://github.com/GedamuA/DANet/assets/30148450/d4539627-312e-4909-9ea1-b2f0f0e0e222)


- DANet Attention weights( camera 3 (side view)).
![image](https://github.com/GedamuA/DANet/assets/30148450/99b02812-52c0-4417-94d0-468a231d0784)

- DANet Attention weights (Drinking water)
![image](https://github.com/GedamuA/DANet/assets/30148450/23a2511f-a1f7-4c5f-81d1-57b57f9b8673)

- DANet Attention weights (Hugging other person)
![image](https://github.com/GedamuA/DANet/assets/30148450/a4e2c92d-187a-4ce8-80b6-3d3433399ea5)

- DANet Attention weights (Hand-shaking).
![image](https://github.com/GedamuA/DANet/assets/30148450/fd43b5b8-212c-453a-a41c-f04e5fb97327)


 ## Acknowledgements
 This repo is based on [2s-AGCN](https://github.com/lshiwjx/2s-AGCN) and [ST-TR](https://github.com/). The data processing is borrowed from [SGN](https://github.com/microsoft/SGN)

Thanks to the original authors for their work!

# Contact
For any questions, feel free to contact: `alemugedamu@gmail.com`
