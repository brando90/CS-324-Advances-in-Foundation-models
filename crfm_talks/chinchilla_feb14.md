# Chinchilla - David Hall - Training Compute-Optimal Large Language Models

## Summary
- 2 sentence summary
  - 
  - 

Abstract:

Paper: 

My summary of the abstract:

FMs summary:

Copypaste summary:

Main contributions:

refs:



## Notes

- notes
  - log-log plots can make things confusing/hide results
    - cuz of linear visually
  - lr adjusted to your steps is better
    - david hall and john thickstun have opposite experience :/ 
      - to what size model did david & john train?
    - perhaps trust deep mind more due to larger models?
    - they are also different data :(, wonder how much that matters
      - what is the difference in data?
        - david hall & john thickstun: ?
        - deep mind: ?
    - differences from Copher
      - upsample books & code
      - consequently downsample wikipedia, webtext
      - slightly better tokenizer
        - Q what does better tokenizer mean?
      - this helps with maths & chemistry
  - Noticed, that since I don't understand what flops means we aren't including it
  in my analysis, this might be a mistake
  - zach, 1/2 optimal?
    - a, b, review what they are more carefully
  - if you change the pre-training data then you have to **fix the eval set**
    - since changing the data set changes "the game"
    - this is for fitting the loss function with some functional scaling laws 

L^(N, D) = E + A*N^-alpha + B*D^-beta 

- E: The first term captures the loss for an ideal generative process on the data distribution, and should
correspond to the entropy of natural text.
- A*N^-alpha: The second term captures the fact that a perfectly trained transformer with 𝑁 parameters underperforms the ideal generative process. 
- B*D^-beta: The final term captures
the fact that the transformer is not trained to convergence, as we only make a finite number of
optimisation steps, on a sample of the dataset distribution.

- Model scaling lows loss: To estimate (𝐴, 𝐵, 𝐸, 𝛼, 𝛽), we minimize the Huber loss (Huber, 1964) between the
predicted and observed log loss using the L-BFGS algorithm.
  - min_{a,b,e,alpha,beta} sum_{runs i} Huber_{delta}(log(L^(N_i, D_i)) - log L_i)) 
- delta = 10^-3
- The Huber loss (𝛿 = 10−3) is robust to outliers, which we find important for good predictive performance over
held-out data points.

- you fix the amount of compute/flops from the top

- You are practicing scaling to a billions


##

Q1: So does MLP dominate or the n^2 self-attention dominate?
A1:

Q2: What is a FLOP? Is it like amount of total compute steps say?
A2:

Q3: What is a different scaling law to fit the (llm, size, tokens) data? 
Adding curvature?
A3:

Q4: why do we want to add curvature if the scaling laws are already scaling laws
i.e. have curvature e.g. y = Ax^b -> lny = lnA + b ln x.
A4:

Q5: Ask david, how does this relate to broken nearl scaling laws?
What are David's thoughts of that paper?
A5:

Q6: Why is the huber loss robust to outliers?
A6:

Q7: What does Zach mean by "theory"? Which theory?
A7:










