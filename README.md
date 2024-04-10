# Introduction

This repo houses experimental code for SuperSTAR.

# Methodology

**The Problem**: ReST (and its variants) are competitive with but quite at the level of SOTA RL fine-tuning algorithms (PPO, DPO). We identify two main problems:
1. ReST can severly overfit to the reward model during RLHF. This is evident in the final human evaluation done in the original ReST paper.
2. ReST does not incorporate granular step-level feedback like PPO can. This puts at a disadvantage when a Process based reward model (**PRM**) is available.

**Solutions**:
1. To address reward model overfit we will experiment with a simple KL penalty during fine-tuning. This can be insereted either during the training phase (a la PPO) or during the dataset curation phase.
2. To incorporate step-level PRM feedback we can try fine-tuning on high-reward prefixes above a certain reward threshold *T*.

# Infrastructure

Training framework TBD:
- Axolotl
- trlX
- custom HF script

Eval framework TBD:
- MATH
- lm-eval-harness?
- MTBench? Other instruction following benchmarks?
