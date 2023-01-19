# Lec 

## Summary
- 2 sentence summary
  - 
  - 

Abstract:

Paper: 

My summary of the abstract:
- training a FM is expensive so decentralized trains it quicker and lowers cost (not confident of my summary)

FMs summary:

Copypaste summary:
- paper1
  - Training foundation models, such as GPT-3 and PaLM, can be extremely expensive, often involving tens
of thousands of GPUs running continuously for months.
  - These models are typically trained in specialized clusters featuring fast, homogeneous interconnects and using carefully designed software systems that
  support both data parallelism and model/pipeline parallelism. Such dedicated clusters can be costly and
  difficult to obtain. Can we instead leverage the much greater amount of decentralized, heterogeneous, and
  lower-bandwidth interconnected compute?
  - In this paper, we present the first study of training large foundation models with model
parallelism in a decentralized regime over a heterogeneous network.
  - **Our key technical contribution is a
scheduling algorithm that allocates different computational “tasklets” in the training of foundation models
to a group of decentralized GPU devices connected by a slow heterogeneous network.**
  - different scenarios for learning over geo-distributed devices simulated using real-world network measurements.
  - **In the most extreme case, across 8 different cities
spanning 3 continents, our approach is 4.8× faster than prior state-of-the-art training systems (Megatron).**

- paper2
  - . We evaluated AC-SGD to fine-tune language models with up to 1.5 billion parameters,
compressing activations to 2-4 bits. AC-SGD provides up to 4.3× end-to-end speed-up in slower networks,
without sacrificing model quality
  - draw back: seems they focus on guarantees to much, I don't care about perfect theoretical guarantees, I care about 
  empirically verifiable/falsifiable results/improvements/theory
  - Contribution 4. We then conduct extensive experiments on sequence classification and language modeling
datasets using DeBERTa-1.5B and GPT2-1.5B models, respectively. We show that AC-SGD can aggressively
compress activations to 2-4 bits without sacrificing convergence performance, where direct quantization of
activations fails to converge; in slow networks, AC-SGD achieves up to 4.3× end-to-end speedup.
  - Contribution 5. Last but not least, we also show that AC-SGD can be combined with state-of-the-art gradient
compression algorithms to enable “end-to-end communication compression”: All data exchanges between
machines, including model gradients, forward activations, and backward gradients are compressed into lower
precision. This provides up to 4.9× end-to-end speed-up, without sacrificing model quality.

- main points:
  - 

refs:
Decentralized Training of Foundation Models in Heterogeneous Environments.Links to an external site.
https://arxiv.org/abs/2206.01288

Fine-tuning Language Models over Slow Networks using Activation Quantization with GuaranteesLinks to an external site.
https://arxiv.org/abs/2206.01299

## Notes

- misc info:
  - querying openai api for embeddings: https://openai.com/blog/new-and-improved-embedding-model/

# Question

Q1: curious, when is decentralized training is actually needed. e.g. I was told recently that small batch size is better to train + models like CLIP fit in a V100 32GB single machine. So when is decentralized training needed? Is it only when the model has to be shared? Does larger batch size actually help or is it better smaller batch size very often updates useful?
A1: 
Eg GPT3 175B in fp16 is 350GB weights. Adam optimizer state triples total size to over a TB. 
So you need many A100 40GB or 80GB to just fit it. 
Then you want to fit enormous batch sizes for activations.
 think the smallest useful model is around 30B? So that's roughly 180GB which needs at least three A100 80GB 
at the bare minimum. gpt3 

Q3:
Hi Professor Zhang,

First of all thank you for your time and sharing your knowledge with us at CS 324.

There is a very basic thing about training a foundation model that I don't understand that was evidenced by your talk. 

Question:
I don't understand why we need distributed training at all at the node level. My understanding is that unless we need to shard the model, we can train everything on a single machine. e.g. CLIP fits in a V100 32GB. 
In addition, it seems from nonGPT we know small batch sizes are sufficient to train (reference https://github.com/karpathy/nanoGPT but I did ask Karpathy directly to confirm  https://github.com/karpathy/nanoGPT/issues/58).
If this is true (models don't have to be so large e.g. CLIP, Chinchilla) and if it's sufficient to get a great foundation model with a small batch size -- then why do we need distributed training (of any type at all?)
My apologize if I am missing something obvious, but I wanted to clear this up in my head since it seems to be a foundation thing in training foundation models (no pun intended).
I'm sure I'm making some wrong assumption, but can't find what, besides that GPT2 isn't a "real" foundation model. A proxy I personally use for foundation model is if they have emergence bevaiour -- my favorite being In Context Learning. 


Thanks for your time again.


Sincerely, Brando Miranda 
A3: