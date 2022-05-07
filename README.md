# [SiameseTracking4UAV]
# Siamese Object Tracking for Unmanned Aerial Vehicle: A Review and Comprehensive Analysis

### Changhong Fu, Kunhan Lu, Guangze Zheng, Junjie Ye, Ziang Cao, and Bowen Li

This code library gives our experimental results and most of the publicly available Siamese trackers.

The trackers are in folder **experiments** and the results are in **results**.

The submitted version of our paper has been uploaded to arXiv which can be found at:

https://arxiv.org/abs/******.

If you want to use our experimental results or related content, please cite our paper using the format as follows:

@ARTICLE{******}

## Results_OPE_AGX

The trackers are tested on the following platform.

- Ubuntu 18.04
- 8-core Carmel ARM v8.2 64-bit CPU
- 512-core Volta GPU
- 32G RAM
- CUDA 10.2
- Python 3.6.3
- Pytorch 0.7.0/1.6.0

**All the Siamese trackers' results are obtained using an NVIDIA Jetson AGX Xavier.**

## Figures

Here shows some of the tracking results of 19 SOTA Siamese trackers.

Comparison of the performance under all the six authoritative UAV tracking benchmarks.
<img src="./figures/Precision and FPS.png">

<img src="./figures/Normalized Precision and FPS.png">

<img src="./figures/Success and FPS.png">

The average performance comparison of the five real-time Siamese trackers under all the six authoritative UAV tracking benchmarks.
<img src="./figures/Attributes.png">

## Environment setup
This code has been tested on an  NVIDIA Jetson AGX Xavier with Ubuntu 18.04, Python 3.6.3, Pytorch 0.7.0/1.6.0, CUDA 10.2.

Please install related libraries before running this code: 
```bash
pip install pyyaml yacs tqdm colorama matplotlib cython tensorboardX easydict
```

## Test

Download pretrained models form the links in `experiments` directory or download pretrained models from official code site and put them into `experiments` directory.

Download testing datasets and put them into `test_dataset` directory. If you want to test the tracker on a new dataset, please refer to [pysot-toolkit](https://github.com/StrangerZhang/pysot-toolkit) to set test_dataset.

Take the test of SiamAPN as an example:

```
python tools/test_siamapn.py                      \
  --dataset UAVTrack112                           \ # dataset_name
  --datasetpath ./test_dataset                    \ # dataset_path
  --config ./experiments/SiamAPN/config.yaml      \ # tracker_config
  --snapshot ./experiments/SiamAPN/config.yaml    \ # tracker_model
  --trackername SiamAPN                             # tracker_name
```

The testing result will be saved in the `results/<dataset_name>/<tracker_name>` directory.

The settings required by different trackers will be different. For details, please refer to the examples in 'tools/test.sh'

## Evaluation 

If you want to evaluate the trackers mentioned above, please put those results into `results` directory as `results/<dataset_name>/<tracker_name>`.

```
python tools/eval.py                              \
  --dataset UAVTrack112                           \ # dataset_name
  --datasetpath path/of/your/dataset              \ # dataset_path
  --tracker_path ./results                        \ # result_path
  --tracker_prefix 'SiamAPN'                        # tracker_name
```


## Acknowledgements
- The code is implemented based on [pysot](https://github.com/STVIR/pysot). We would like to express our sincere thanks to the contributors.

- We would like to thank Jilin Zhao, Kunhui Chen, Haobo Zuo and Sihang Li their help in building this code library.

- We also thank the contribution of Matthias Muller, Siyi Li, Dawei Du, Heng Fan, and Changhong Fu for their previous work of the benchmarks UAV123@10fps, UAV20L, DTB70, UAVDT, VisDrone-SOT2020, and UAVTrack112. Their papers and benchmark address are listed here.

### UAV123@10fps & UAV20L

Paper: A Benchmark and Simulator for UAV Tracking

Paper site: https://link.springer.com/chapter/10.1007%2F978-3-319-46448-0_27 .

Code and benchmark site: https://cemse.kaust.edu.sa/ivul/uav123 .

### DTB70

Paper: Visual Object Tracking for Unmanned Aerial Vehicles: A Benchmark and New Motion Models

Paper site: https://dl.acm.org/doi/10.5555/3298023.3298169 .

Code and benchmark site: https://github.com/flyers/drone-tracking .

### UAVDT

Paper: The Unmanned Aerial Vehicle Benchmark: Object Detection and Tracking

Paper site: https://link.springer.com/article/10.1007/s11263-019-01266-1 .

Code and benchmark site: https://sites.google.com/site/daviddo0323/projects/uavdt .

### VisDrone-SOT2020

Paper: VisDrone-SOT2020: The Vision Meets Drone Single Object Tracking Challenge Results

Paper site: https://link.springer.com/chapter/10.1007/978-3-030-66823-5_44 .

Code and benchmark site: http://aiskyeye.com/ .

### UAVTrack112

Paper: Onboard Real-Time Aerial Tracking With Efficient Siamese Anchor Proposal Network

Paper site: https://ieeexplore.ieee.org/abstract/document/9477413 .

Code and benchmark site: https://github.com/vision4robotics/SiamAPN .
