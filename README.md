# Introduction

This repo houses experimental code for SuperSTAR.

# Methodology

**The Problem**: ReST (and its variants) are competitive with but quite at the level of SOTA RL fine-tuning algorithms (PPO, DPO). We identify two main problems:
1. ReST can severly overfit to the reward model during RLHF. This is evident in the final human evaluation done in the original ReST paper.
2. ReST does not incorporate granular step-level feedback like PPO can. This puts it at a disadvantage when a Process based reward model (**PRM**) is available.

**Solutions**:
1. To address reward model overfit we will experiment with a simple KL penalty during fine-tuning. This can be insereted either during the training phase (a la PPO) or during the dataset curation phase.
2. To incorporate step-level PRM feedback we can try fine-tuning on high-reward prefixes above a certain reward threshold *T*.

# Infrastructure

Training: Huggingface trainer
Inference: [vllm](https://github.com/vllm-project/vllm)
Evaluation: 
- MATH dataset (use EleutherAI eval harness?, If this doesn't work I also have my own custom eval code)
- What are some popular benchmarks for RLHF evaluation
  - MTbench?
  - LLMArena?
  - AlpacaFarm?
  - ???
