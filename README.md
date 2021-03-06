# NJUNMT-pytorch

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

NJUNMT-pytorch is an open-source toolkit for neural machine translation.
This toolkit is highly research-oriented, which contains some common baseline
model:

- [DL4MT-tutorial](https://github.com/nyu-dl/dl4mt-tutorial): A rnn-base nmt model widely used as baseline. To our knowledge, this is the
only pytorch implementation which is exactly the same as original model.([nmtpytorch](https://github.com/lium-lst/nmtpytorch) is another pytorch implementation but with minor structure difference.)

- [Attention is all you need](https://arxiv.org/abs/1706.03762): A strong nmt model introduced by Google, which only relies on attenion
mechanism. Our implementation is different from the official [tensor2tenosr](https://github.com/tensorflow/tensor2tensor)


# Requirements

- python 3.5+
- pytorch 3.1
- tqdm
- tensorboardX

# Usage

## Data Preprocessing

See help of ```./data/build_dictionary.py```

Vocabulary will be stored as json format.

We highly recommend not to set the limitation of the number of
words and control it by config files while training.

## Configuration

See examples in ```./configs``` folder. You can reproduce our
Chinese-to-English Baseline by directly using those configures.

```loss_schedule_config.yaml``` is the configure file using
valid loss as schedule criterion.

```noam_schedule_config.yaml``` is the configure file using
schedule method in google's paper.

```dl4mt_config.yaml```

## Training
See training script ```./scripts/train.sh```

## Translation
See translation script ```./scripts/translation.sh```

# Benchmark

See [BENCHMARK.md](./BENCHMARK.md)

# Q&A

1. What is ```shard_size``` ?

```shard_size``` is trick borrowed from OpenNMT-py, which

could make large model run in the memory-limited condition.

For example, you can run wmt17 EN2DE task on a 8GB GTX1080 card

with batch size 64 by setting ```shard_size=10```

2. What is ```use_bucket``` ?

When using bucket, parallel sentences will be sorted partially
according to the length of target sentence.

Set this option to ```true``` will bring considerable improvement
but performance regression.

# Acknowledgement

- This code is heavily borrowed from OpenNMT/OpenNMT-py and have been
simplified for research use.




