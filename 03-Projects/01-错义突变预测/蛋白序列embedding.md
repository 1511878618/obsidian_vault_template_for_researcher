DNA，蛋白质序列的embedding方法有很多，这里进行简单的汇总

[bio_embedding]([https://github.com/sacdallago/bio_embeddings](https://github.com/sacdallago/bio_embeddings))提供了对所有embedding方法调用的API，[官方文档](https://docs.bioembeddings.com/v0.2.3/)可以了解更多。


## Emebdding文章汇总与介绍
Embedding的方法是NLP中常用的套路，word2vec使得embedding的思想发扬光大，并得到广泛的运用，现在的NLP的方法是基于大规模的语言模型BERT类方法进行预训练，随后对下游任务进行fine-tune或者接入decoder进行生成模型的输出。

蛋白质也是一种序列语言，[与NLP类似，蛋白质语言模型(PLM)将整个蛋白质序列解释为一个句子，并将其组成部分--氨基酸--解释为单个单词。蛋白质序列被限制采用为实现特定功能而优化的特定3D结构。这些限制反映了NLP中的语法和意义规则。🔤](zotero://note/u/R5A58A92/)

### ProTrans


### ESM
- ESM[Evolutionary-scale prediction of atomic level protein structure with a language model] (https://www.biorxiv.org/content/10.1101/2022.07.20.500902v3)
- [Language models generalize beyond natural proteins](https://www.biorxiv.org/content/10.1101/2022.12.21.521521v1)

| Shorthand | `esm.pretrained.`           | Dataset | Description  |
|-----------|-----------------------------|---------|--------------|
| ESM-2    | `esm2_t36_3B_UR50D()` `esm2_t48_15B_UR50D()`       | UR50 (sample UR90)  | SOTA general-purpose protein language model. Can be used to predict structure, function and other protein properties directly from individual sequences. Released with [Lin et al. 2022](https://doi.org/10.1101/2022.07.20.500902) (Aug 2022 update). |
| ESMFold   | `esmfold_v1()`         | PDB + UR50 | End-to-end single sequence 3D structure predictor (Nov 2022 update). |
| ESM-MSA-1b| `esm_msa1b_t12_100M_UR50S()` |  UR50 + MSA  | MSA Transformer language model. Can be used to extract embeddings from an MSA. Enables SOTA inference of structure. Released with [Rao et al. 2021](https://www.biorxiv.org/content/10.1101/2021.02.12.430858v2) (ICML'21 version, June 2021).  |
| ESM-1v    | `esm1v_t33_650M_UR90S_1()` ... `esm1v_t33_650M_UR90S_5()`| UR90  | Language model specialized for prediction of variant effects. Enables SOTA zero-shot prediction of the functional effects of sequence variations. Same architecture as ESM-1b, but trained on UniRef90. Released with [Meier et al. 2021](https://doi.org/10.1101/2021.07.09.450648). |
| ESM-IF1  | `esm_if1_gvp4_t16_142M_UR50()` | CATH + UR50 | Inverse folding model. Can be used to design sequences for given structures, or to predict functional effects of sequence variation for given structures. Enables SOTA fixed backbone sequence design. Released with [Hsu et al. 2022](https://doi.org/10.1101/2022.04.10.487779). |

For a complete list of available models, with details and release notes, see [Pre-trained Models](#available-models).