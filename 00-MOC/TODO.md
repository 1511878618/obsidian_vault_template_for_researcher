
## cadFace
1. @iym 为了验证除了**年龄和性别**之外，模型识别的疾病特征。建议做一下case-control matching。也就是，对每一个control，找一个性别相同，年龄相仿的人配对，然后测试模型效果。
> **排除年龄和性别的影响**
> 计算age和output的corr


2. [x] 先跑一下年龄性别等跑一个regession, svm 作为baseline 🛫 2023-08-07
3. [ ] 数据清洗的角度，背景弄掉，只要脸部区域（alter） ⏫ 🛫 2023-08-07
4. [ ] 不按照人进行抽样，正负样本先随机augmentation，然后均匀抽样
5. 固定vit前k个block
6. **原始图片，高分辨率的情况下，分割出不同的面部区域，分别run model。** ⏫ 🛫 2023-08-08
7. 拿FC那一层做t-sne
8. figsize试图用大一点。尝试高精度的。 ⏫ 🛫 2023-08-07
9. **图像解决阴影问题** ⏫ 🛫 2023-08-07
10. 完善readme
11. 添加模型调用脚本

两次CAD是否有关系，时间跨度多大？

> regress掉age和sex，然后计算残差，并计算与label的相关性

提高AUC，模型方法创新。

TODO：
1. **方法学的创新**
2. **target: nature artificial intelligence**
3. 专利
4. **可解释性的故事**





## UKB
1. 如果没有问题我们可以把整个基因组都跑一遍。最先只需要跑这些 traits peaks 周围上下2M的区域就行。

2. LDL, CRP和 alkaline phosphatase

3. pheweb部署