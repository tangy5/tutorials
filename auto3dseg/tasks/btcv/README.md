# BTCV Dataset For Auto3dseg

This repository provides a benmarking guide and recipe to train the template algorithms, validation performance, and is tested and maintained by NVIDIA.



##### Validation performance: NVIDIA DGX-1 (4x V100 32G)

Our results were obtained by running the `python scripts/benchmark.py --mode train --gpus {1,8} --dim {2,3} --batch_size <bsize> [--amp]` training script in the MONAI 0.9.1 container on NVIDIA DGX-1 with (4x V100 32G) GPUs. Performance numbers (in volumes per second) were averaged over an entire training epoch.

| Methods| Dimension | GPUs | Batch size / GPU | Fold 0 | Fold 1 | Fold 2 | Fold 3 | Fold 4|
|:-:|:-:|:---:|:---------:|:-----------:|:--------:|:---------:|:-------------:|
| SwinUNETR | 3 | 4 | 3 | 0.8111 | 0.8011 | 0.6712 | 0.6301 | 0.7239 | 0.7275
| SegResNet | 3 | 4 | 3 | 0.8212 | 0.8115 | 0.6848 | 0.6377 | 0.7368 | 0.7384
| DiNTS | 3 | 8 | 44 | 3 | 0.8058 | 0.7955 | 0.6880 | 0.6281 | 0.7008 | 0.7196
|SegResNet2d | 2 | 4 | 3 | 0.6803 | 0.7498 | 0.6188 | 0.6241 | 0.5848 | 0.6516
