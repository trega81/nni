# ENAS

## Introduction

The paper [Efficient Neural Architecture Search via Parameter Sharing](https://arxiv.org/abs/1802.03268) uses parameter sharing between child models to accelerate the NAS process. In ENAS, a controller learns to discover neural network architectures by searching for an optimal subgraph within a large computational graph. The controller is trained with policy gradient to select a subgraph that maximizes the expected reward on the validation set. Meanwhile the model corresponding to the selected subgraph is trained to minimize a canonical cross entropy loss.

Implementation on NNI is based on the [official implementation in Tensorflow](https://github.com/melodyguan/enas), including a general-purpose Reinforcement-learning controller and a trainer that trains target network and this controller alternatively. Following paper, we have also implemented macro and micro search space on CIFAR10 to demonstrate how to use these trainers. Since code to train from scratch on NNI is not ready yet, reproduction results are currently unavailable.

## Examples

### CIFAR10 Macro/Micro Search Space

[Example code](https://github.com/microsoft/nni/tree/v1.9/examples/nas/enas)

```bash
# In case NNI code is not cloned. If the code is cloned already, ignore this line and enter code folder.
git clone https://github.com/Microsoft/nni.git

# search the best architecture
cd examples/nas/enas

# search in macro search space
python3 search.py --search-for macro

# search in micro search space
python3 search.py --search-for micro

# view more options for search
python3 search.py -h
```

## Reference

### PyTorch

```eval_rst
..  autoclass:: nni.nas.pytorch.enas.EnasTrainer
    :members:

..  autoclass:: nni.nas.pytorch.enas.EnasMutator
    :members:
```
