# Lec Pathways Language Model and Model Scaling - Aakanksha Chowdhery | Stanford MLSys #69

attendance: https://forms.gle/Qow74t8tK4UbMyqV8

## Summary
- 2 sentence summary
  - 
  - 

Abstract:
Large language models have been shown to achieve remarkable performance across a variety of natural language tasks using few-shot learning, which drastically reduces the number of task-specific training examples needed to adapt the model to a particular application. To further our understanding of the impact of scale on few-shot learning, we trained a 540-billion parameter, densely activated, Transformer language model, which we call Pathways Language Model PaLM. We trained PaLM on 6144 TPU v4 chips using Pathways, a new ML system which enables highly efficient training across multiple TPU Pods. We demonstrate continued benefits of scaling by achieving state-of-the-art few-shot learning results on hundreds of language understanding and generation benchmarks. On a number of these tasks, PaLM 540B achieves breakthrough performance, outperforming the finetuned state-of-the-art on a suite of multi-step reasoning tasks, and outperforming average human performance on the recently released BIG-bench benchmark. A significant number of BIG-bench tasks showed discontinuous improvements from model scale, meaning that performance steeply increased as we scaled to our largest model. PaLM also has strong capabilities in multilingual tasks and source code generation, which we demonstrate on a wide array of benchmarks. We additionally provide a comprehensive analysis on bias and toxicity, and study the extent of training data memorization with respect to model scale. Finally, we discuss the ethical considerations related to large language models and discuss potential mitigation strategies.

Paper: 

My summary of the abstract:

FMs summary:

Copypaste summary:
- Large language models have been shown to achieve remarkable performance across a variety of natural language tasks using few-shot learning, which drastically reduces the number of task-specific training examples needed to adapt the model to a particular application.
- we trained a 540-billion parameter, densely activated, Transformer language model, which we call Pathways Language Model PaLM.
- We trained PaLM on 6144 TPU v4 chips using Pathways, a new ML system which enables highly efficient training across multiple TPU Pods.
- We demonstrate continued benefits of scaling by achieving state-of-the-art few-shot learning results on hundreds of language understanding and generation benchmarks.
- outperforming the finetuned state-of-the-art on a suite of multi-step reasoning tasks, and outperforming average human performance on the recently released BIG-bench benchmark.
- again not substatiated claim of discontinuous improvements from model scale
  - A significant number of BIG-bench tasks showed discontinuous improvements from model scale, meaning that performance steeply increased as we scaled to our largest model.
- PaLM also has strong capabilities in multilingual tasks and source code generation
  - although as alycia mentioned, there isn't much multilingual data data...only 22% is non english
- 

- main contributions:
  - Efficient scaling – We demonstrate the first large-scale use of Pathways (Barham et al., 2022) – a new
ML system which enables training a single model across thousands or tens of thousands of accelerator
chips in a highly efficient manner. With Pathways, we trained a 540B parameter language model on
6144 TPU v4 chips at efficiency levels that could not be reached before for models of this scale. Most
previous large language models were either trained on a single TPU system (Du et al., 2021; Thoppilan
et al., 2022) or used pipeline parallelism (Huang et al., 2019) to scale across GPU clusters (Smith et al.,
2022) or multiple TPU v3 pods (Rae et al., 2021), with a maximum scale of 4096 TPU v3 chips. In
Section 4, we describe how we were able to scale pipeline-free training of PaLM 540B to 6144 chips
across two TPU v4 Pods while achieving very high efficiency of 46.2% in model FLOPs utilization
(observed throughput relative to theoretical max throughput) 
  - Continued improvements from scaling: no pleatau as scale increases
  - Discontinuous improvements – To better understand the scaling behavior, we present results at
three different parameter scales: 8B, 62B, and 540B. Typically, scaling from 62B to 540B results in
similar performance as scaling from 8B to 62B, which is consistent with the “power law” rule of thumb
often observed in neural network scaling
  - Multilingual understanding: its good despite only 22% of the data being none english
  - Ok they want to emphasize reasoning, perhaps it was the first paper it did this
    - Another critical takeaway from this work is the breakthrough performance on reasoning tasks, which require
multi-step logical inference. 
      - The results on reasoning tasks are not
achieved through model scale alone, but by a combination of scale and chain-of-thought prompting, where
the model is explicitly prompted to generate a natural language logical inference chain before making its
prediction
    - improvements from scale for few-shot language understanding have not yet plateaued
    - improvements are actually discontinuous, meaning that the improvements from 8B to
62B are very modest, but then jump immensely when scaling to 540B
    - 

refs:
  - https://arxiv.org/pdf/2204.02311.pdf
  - https://ai.googleblog.com/2022/04/pathways-language-model-palm-scaling-to.html


## Notes

- misc info:
  - some thing about the arch that makes it faster, pathways 
  - PaLM is decoder only
  - 540B parameters
  - it's challenging to even serve a 540B model, so it needs parallelism, doesn't fit in a single chip, so communication costs are high
- comments on seminar discussion
  - More recent LLMs, such as GLaM, LaMDA, Gopher, and Megatron-Turing NLG, achieved state-of-the-art few-shot results 
  on many tasks by scaling model size, using sparsely activated modules, and training on larger datasets from more 
  diverse sources.
    - A really coarse intuition is sparse activation means you can get benefits of lots of parameters, but since you’re 
    only calling on some of them during inference, training + inference is faster / cheape
  - explains jokes
  - Second, the breakthrough performance on reasoning tasks (Section 6.3) has critical implications. It is obvious
that a model being able to generate natural language to explain its predictions is beneficial to the end user of
a system, in order to better understand why a model made a certain prediction.

# Question

Q1: What is the main contribution of PaLM? System design or model/arch design?
A1: 

Q2: The PaLM blogpost states that "PaLM also shows strong performance on multilingual NLP benchmarks, including 
translation, even though only 22% of the training corpus is non-English." What is your intuition for this 
(i.e. do these multilingual NLP benchmarks primarily consist of sister languages of English)? What does 
"strong performance" mean / how does performance compare to SOTA?
A2: guesses from Aakanksha; languages share rules, coming from common roots, so it's easier to learn (perhaps).

Q3: When does scale not help?
A3:

Q4: Does fine tuning make things worse?
A4:

Q5: why is gpt3 missing again from the comparison?
A5:

Q6: from these reasoning tasks, since the output is informal language, how do you extract the answer systematically from
thousand of examples to evaluate a 0-1 error/accuracy correctly?
A6:

Q7: do these models suffer from catastrophic forgetting when fine tuned? has this been empirically evaluated?
A7:

Q8: is this correct feeling -- but it feels GPT3 is better than PaLM. Is this true?
A8:

Q9: what is the difference between a TPU pod and a GPU graphics card? What does the word pod mean?
A9: My understanding is that a pod means a cluster of TPU chips (3,072 chip per pod). The chip here might be similar to a GPU card. 
https://cloud.google.com/tpu/docs/training-on-tpu-pods
A TPU Pod is a collection of TPU devices connected by dedicated high-speed network interfaces. A TPU Pod allows you to 
distribute the processing load across multiple TPUs. Each TPU board is connected to a high-performance CPU-based 
host machine for things like loading and preprocessing data.

sorry, yes. That was confusing. I was tyring to see how much 1 tpu chip it takes to do the ML work 1 gpu card does.
Like the number above makes it hard to appreciate the PaLM work given I only ever use if Im lucky, 8 A100 GPUs with 80GBs

I see. For your original question, I think the term pods is the smallest subdivision of a unit that you can get on a TPU. And they are using this arbitrary unit since one TPU board is huge and contains multiple sub units


