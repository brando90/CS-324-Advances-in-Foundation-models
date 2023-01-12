# Lec2 flash attention: 

## Flash Attention:
Abstract:
Transformers are slow and memory-hungry on long sequences, since the time and memory complexity of self-attention are quadratic in sequence length. Approximate attention methods have attempted to address this problem by trading off model quality to reduce the compute complexity, but often do not achieve wall-clock speedup. We argue that a missing principle is making attention algorithms IO-aware -- accounting for reads and writes between levels of GPU memory. We propose FlashAttention, an IO-aware exact attention algorithm that uses tiling to reduce the number of memory reads/writes between GPU high bandwidth memory (HBM) and GPU on-chip SRAM. We analyze the IO complexity of FlashAttention, showing that it requires fewer HBM accesses than standard attention, and is optimal for a range of SRAM sizes. We also extend FlashAttention to block-sparse attention, yielding an approximate attention algorithm that is faster than any existing approximate attention method. FlashAttention trains Transformers faster than existing baselines: 15% end-to-end wall-clock speedup on BERT-large (seq. length 512) compared to the MLPerf 1.1 training speed record, 3× speedup on GPT-2 (seq. length 1K), and 2.4× speedup on long-range arena (seq. length 1K-4K). FlashAttention and block-sparse FlashAttention enable longer context in Transformers, yielding higher quality models (0.7 better perplexity on GPT-2 and 6.4 points of lift on long-document classification) and entirely new capabilities: the first Transformers to achieve better-than-chance performance on the Path-X challenge (seq. length 16K, 61.4% accuracy) and Path-256 (seq. length 64K, 63.1% accuracy).

This work received the Best Paper Award at the Hardware-Aware Efficient Training Workshop at ICML, 2022. FlashAttention is now widely used in some of the largest research labs and companies, in just 6 months after its release.

Paper: https://arxiv.org/abs/2205.14135

My summary of the absract:

FMs summary:
todo

Copypaste summary:
- We argue that a missing principle is making attention algorithms IO-aware -- accounting for reads and writes between levels of GPU memory. We propose FlashAttention, an IO-aware exact attention algorithm that uses tiling to reduce the number of memory reads/writes between GPU high bandwidth memory (HBM) and GPU on-chip SRAM.
- We also extend FlashAttention to block-sparse attention, yielding an approximate attention algorithm that is faster than any existing approximate attention method.
- FlashAttention and block-sparse FlashAttention enable longer context in Transformers, yielding higher quality models (0.7 better perplexity on GPT-2 and 6.4 points of lift on long-document classification) and entirely new capabilities

## Notes

- main points:
  - flash attention is not an approximation, it produces exact attention
  - problem they solve: faster attention computation using hardware aware ideas to compute exact attention
  - gist of main idea/technique:
  - cool conclusion/results: 

- misc info:
  - they did longer contexts & that reduced perplexity
  - But the memory-efficiency allows us to learn over longer contexts (the time-efficiency also makes training over these long sequences practical, e.g., don't need to wait around for many days)

- 2 sentence summary
  - We chop up attention into smaller blocks that fit in SRAM so that all operations can be calculated in the SRAM at once without moving it in and out of SRAM-HBM
  - This uses less memory bandwidth & faster, which allows longer contexts & better performance

# Question

Q1: The abstract of the current speakers starts by saying that self-attention takes quadratic workload. 
To my understanding of what I've been told is that this might not actually be true. Reference https://arxiv.org/abs/2112.05682 
paper title is Self-attention Does Not Need O(n2) Memory, may this be clarified and it's relation to the speakers work? Thanks in advance!
A1: Seems that flash attention uses the trick from that paper. Just somehow don't materialize the entire matrix and do
the compute. Something to do with block size etc. 

Q2: does flash attention affect only forward pass?
A2: Both. The blocking is applied on both passes, while the recomputation is only used in the backward pass to 
calculated the gradient

Q3: How compatible is using an alternative matrix multiplication algorithm, such as those identified by AlphaTensor, with FlashAttention? https://www.nature.com/articles/s41586-022-05172-4#author-information
A3: 

Q4: FlashAttention, what is a block-size? Why does it matter for speed ups.
A4: 

Q5: what is "wall-clock speedup"?
A5: 

Q6: what is tiling?
A6:

Q7: what is a one or two sentence summary of the main technique that leads to all these awesome benefits?
A7: 