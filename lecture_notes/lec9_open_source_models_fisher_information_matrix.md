# Lec - Building ML Models like Open-Source Software - Colin Raffel | Stanford MLSys #72 

attendance: https://forms.gle/Qow74t8tK4UbMyqV8
webpage: https://stanford-cs324.github.io/winter2023/
canvas: https://canvas.stanford.edu/courses/169201
youtube mlsys playlist: https://www.youtube.com/playlist?list=PLSrTvUm384I9PV10koj_cqit9OfbJXEkq

## Summary
- 2 sentence summary
  - 

Abstract:
Abstract:
Pre-trained models have become a cornerstone of modern ML pipelines thanks to the fact that they can provide improved performance with less labeled data on downstream tasks. However, these models are typically created by a resource-rich research group that unilaterally decides how a given model should be built, trained, and released, after which point it is left as-is until a better pre-trained model comes along to completely supplant it. In this talk, I will present a vision for building machine learning models in the way that open-source software is developed - by a distributed community of contributors who iteratively build valuable artifacts through a mature set of tools including version control, continuous integration, merging, and more.

Paper: 

My summary of the abstract:

FMs summary:
- The speaker presents a vision for the development of machine learning models to be more like open-source software, with a community of contributors building models using tools like version control and continuous integration. This aims to address the current issue of pre-trained models being created by a single resource-rich group and left unchanged until replaced.
- 

Copypaste summary:

Main contributions:

refs:

## Notes

- misc info:
  - if a data point appears again then the model predicts it more often! :O
    - can my diversity data set detect this? 
    - Or at least show the more duplication the less diversity?
    - FIM = parameters that are most important
      - why is that a good intuition for what FIM measures?
    - using FIM matrix, they can fine tune much less of the number parameters -- using FISH mask -- they can get much
    more effective fine tuning
      - does he have an implementation of FISH mask that works with pytorch or HF?
  - Posterios = Pr[Theta | Data]
  - Fisher merging
    - use fisher matrices to merge models e.g. sum_i fisher_i lambda_i model_i / sum_i fisher_i lambda_`
  - Fisher Mask: https://arxiv.org/abs/2111.09839
  - diff of black box combinatorials
    - what does the author think of black box gradient estimation that does NOT use RL like this: https://arxiv.org/abs/1912.02175 ?

FIM:
```
The Fisher Information Matrix (FIM) measures the amount of information that the data contains about the parameters of a statistical model. In other words, it represents the sensitivity of the data with respect to the model parameters. The FIM provides a measure of the precision of the parameters, which is the inverse of the variance.

If the FIM is large for a particular parameter, it means that the data is sensitive to that parameter, and small changes in the value of that parameter will result in large changes in the likelihood. This implies that the data provides strong constraints on that parameter and the estimate of its value will be precise. On the other hand, if the FIM is small for a parameter, it means that the data provides weak constraints on that parameter, and small changes in its value will result in only small changes in the likelihood. This implies that the estimate of its value will be less precise.

Therefore, the parameters with large entries in the FIM are those that are most important in the model, as they are the most strongly constrained by the data. The parameters with small entries in the FIM are those that are less important, as they are less strongly constrained by the data. The FIM provides a useful tool for understanding the structure of a model and the relative importance of its parameters.
```

  - given a model was fine tuned in this open source model thing, how does one evaluate models cheaply
  - Zulip for open source models: https://zulip.com/
  - 

# Question

Q1: May the speaker explain in more detail why intuitively the Fisher Information Matrix (FIM) approximately measures 
what parameters are most important?
A1: 

Q2: Does the speaker have an implementation of FISH mask that works with pytorch or HF?
A2: https://github.com/varunnair18/FISH 

Q3: what does the author think of black box gradient estimation that does NOT use RL like this: https://arxiv.org/abs/1912.02175 ?
A3:

Q4: how much evidence is there that (huge) foundation models catastrophically forget (if at all) given how massive they are -- even when fine tunned? (my hypothesis is that not much, due to how large + how large loss they achieve at the end of training so it suggests there is still lots of space for further training)
A4:

Q5: what does he mean that SGD is worse than averaging
A5:
