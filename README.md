# Zari model checkpoints

This directory contains the Zari checkpoints from our work, **Measuring and
Reducing Gendered Correlations in Pre-trained NLP Models**, presented as a [blog
post](https://ai.googleblog.com/2020/10/measuring-gendered-correlations-in-pre.html)
and written up as a [paper](https://arxiv.org/abs/2010.06032). Zari checkpoints
are derived from [BERT](https://github.com/google-research/bert) and
[ALBERT](https://github.com/google-research/albert) model checkpoints,
trained to reduce gendered correlations being learned in pre-training. To do
this, we use two techniques:

* **Dropout** models were initialized from the relevant publicly-available
  checkpoint and pre-training continued over Wikipedia, with increased dropout
  rate.
* **CDA** models were pre-trained from scratch over Wikipedia. Word
  substitutions for data augmentation are determined using the word lists
  provided at [corefBias](https://github.com/uclanlp/corefBias) ([Zhao et
  al. (2018)](https://arxiv.org/abs/1804.06876)).

Four pre-trained models are provided in this release:

* [**bert-dropout**](https://storage.googleapis.com/bert_models/filbert/2020_10_13/zari-bert-dropout.tar.gz)
  Trained from [BERT Large Uncased](https://storage.googleapis.com/bert_models/2018_10_18/uncased_L-24_H-1024_A-16.zip),
  with `attention_probs_dropout_prob=0.15` and
  `hidden_dropout_prob=0.20`.
* [**bert-cda**](https://storage.googleapis.com/bert_models/filbert/2020_10_13/zari-bert-cda.tar.gz)
  Trained with BERT Large Uncased config, with an augmented dataset, for 1M steps.
* [**albert-dropout**](https://storage.googleapis.com/albert_models/zari-albert-dropout.tar.gz)
  Trained from [Albert Large](https://storage.googleapis.com/albert_models/albert_large_v2.tar.gz),
  with `attention_probs_dropout_prob=0.05` and
  `hidden_dropout_prob=0.05`.
* [**albert-cda**](https://storage.googleapis.com/albert_models/zari-albert-cda.tar.gz)
  Trained with Albert Large config, with an augmented dataset, for 125k steps.

If you use these models in your work, kindly cite:

```
@misc{zari,
      title={Measuring and Reducing Gendered Correlations in Pre-trained Models},
      author={Kellie Webster and Xuezhi Wang and Ian Tenney and Alex Beutel and Emily Pitler and Ellie Pavlick and Jilin Chen and Slav Petrov},
      year={2020},
      eprint={2010.06032},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```