#自交不亲和性 #课题

[deeprank-GNN](https://github.com/DeepRank/Deeprank-GNN)，是基于GNN的模型，参考意义有但不大，文档不完善。

1. [msms](https://ccsb.scripps.edu/msms/) 用于计算分子表面
>_MSMS_ is a fast algorithm for computing molecular surfaces. It was developed by Dr. Michel F. Sanner as part of his PhD thesis. It has been widely used for computing and displaying Solvent Excluded Surfaces for proteins also knows as the Lee and Richards (who first defined the concept of rolling a probe representing a solvent molecule over the set of sphere representing protein atoms, or the Connolly surface as Mike Connolly wrote the first implementation of a program to compute this surface analytically. MSMS is used by various molecular visualization programs including VMD, Chimera, and our own PMV. It is also available as a standalone binary on the download page as well as a library with Python binding available it the MGLTools and ADFRsuite software distributions.

2.  [FreeSASA]是计算分子表面溶剂可及性的工具，  [FreeSASA github repo](https://github.com/mittinatten/freesasa)。Python版本直接`pip install freesasa`即可

## 安装

```shell
conda create -n deeprank python=3.8

pip install torch DeepRank-GNN  #如果报错，先装pytorch

conda install msms  # 用于计算分子表面能

pip install freesasa  #计算表面溶剂可及性

pip install matplotlib  # 正常来说不缺

```

