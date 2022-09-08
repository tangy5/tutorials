# BTCV Dataset For Auto3dseg

This repository provides a benmarking guide and recipe to train the template algorithms, validation performance, and is tested and maintained by NVIDIA.



##### Training performance: NVIDIA DGX-1 (8x V100 16G)

Our results were obtained by running the `python scripts/benchmark.py --mode train --gpus {1,8} --dim {2,3} --batch_size <bsize> [--amp]` training script in the MONAI 0.9.1 container on NVIDIA DGX-1 with (4x V100 32G) GPUs. Performance numbers (in volumes per second) were averaged over an entire training epoch.

| Dimension | GPUs | Batch size / GPU | Throughput - mixed precision [img/s] | Throughput - FP32 [img/s] | Throughput speedup (FP32 - mixed precision) | Weak scaling - mixed precision | Weak scaling - FP32 |
|:-:|:-:|:---:|:---------:|:-----------:|:--------:|:---------:|:-------------:|
| 2 | 1 | 64 | 607.16 | 298.84 | 2.032 | N/A | N/A |
| 2 | 1 | 128 | 653.44 | 307.01 | 2.128 | N/A | N/A |
| 2 | 8 | 64 | 4058.79 | 2196.05 | 1.848 | 6.685 | 7.349 |
| 2 | 8 | 128 | 4649.37 | 2388.46 | 1.848 | 7.115 | 7.779 |
| 3 | 1 | 1 | 8.66 | 1.99 | 4.352 | N/A | N/A |
| 3 | 1 | 2 | 9.65 | 2.07 | 4.662 | N/A | N/A |
| 3 | 1 | 4 | 9.99 | OOM | N/A | N/A | N/A |
| 3 | 8 | 1 | 58.45 | 15.55 | 3.756 | 6.749 | 7.819 |
| 3 | 8 | 2 | 66.03 | 16.22 | 4.071 | 6.842 | 7.835 |
| 3 | 8 | 4 | 67.37 | OOM | N/A | 6.743 | N/A |