# Lec data-centric perspective on reliable generalization - ludwig schmidt

attendance: https://forms.gle/Qow74t8tK4UbMyqV8
webpage: https://stanford-cs324.github.io/winter2023/
canvas: https://canvas.stanford.edu/courses/169201

## Summary
- 2 sentence summary
  - more reliable under distribution shift, yet there is still large room for improvement. Are better training algorithms or training data the more promising way forward?
  - YES DATA OR ALGORITHMS?
    - we study this question in the context of computer vision and OpenAI’s CLIP model for learning from image-text data.
  - we survey the current robustness landscape based on a large-scale experimental study involving more than 200 different models and test conditions. The CLIP models stand out with unprecedented robustness gains on multiple challenging distribution shifts.
  - clip most robust model across 200 models
  - To further improve CLIP, we then introduce new methods for reliably fine-tuning models by interpolating the weights of multiple models.
  - we investigate the cause of CLIP’s robustness via controlled experiments to disentangle the influence of language supervision and training distribution. 
    - so what is the answer?
    - partial vague answer: While CLIP leveraged large scale language supervision for the first time, its robustness 
      - **actually comes from the pre-training dataset.**

Abstract:

Paper: 

My summary of the abstract:

FMs summary:

Copypaste summary:

Main contributions:

refs:

## Notes

- misc info:
  - imagenet models don't generalize well to other datasets!?
  - definition of robustness:
    - something a human CAN do why can't my model can't?
  - seems the progress came from CLIP in robustness i.e. generalizing to other data sets e.g. imagneet to imagenetV2
  - it is also about the quality of data sets
    - show him my work?
    - yes! 
  - recap clip
    - training data: 400M images, collected fro the web (dataset internal to OpenAI)
    - Compute: training on 250-600 GPUs for 18 days ~ 18/7 = 2.5 weeks
    - Model: ResNets and ViTs with up to 300M parameters
    - training algorithm:
      - image text pairs with captions
      - (text, image) pairs
      - contrastive loss = (img, text) pairs that are close together have a similar embedding, the ones that don't match
      train the embedding to be far apart (standrd contrastive training)
    - you can do zero shot classification
      - embedd label (e.g. text), embed all labels you want to consider -> produces an embedding x_text/x_label
        - text = "a photo of a (<object name>)"
        - x_text/label
      - embedd image -> produces an embedding x_img
        - x_img
      - label = classification = max( comparison(x_text, x_img) )
        - produce the label that is most similar btw the embedding image given and all the texts (with the label)
    - this halfs the distance to y = x! i.e. really robust
    - Q: does it mean anything to do this in reverse?
    - fine tuning on imagenet reduces robsutness!
      - WHY!? interesting
    - yes we can do fine tuning without doing robustness
      - interpolate the zero shot and the fine tuned model... odd!
      - 0.5 is basically the best
    - weird why would linear interpolation of weights of a non linear model work so well?
    - model soup
      - average lots of models
    - Qs class:
      - 
    - Q: where does CLIP's robustness come from? -> training data

# Question

Q1: we investigate the cause of CLIP’s robustness via controlled experiments to disentangle the influence of language supervision and training distribution. So what's the answer?
A1: 

Q2: why is the y=x line important in the curve Ludwig has?
A2: y = x means that it's perfectly robust, since the generalization error/acc for original imagenet is the same for
the imagnetV2 dataset.

Q3:
    - you can do zero shot classification
      - embedd label (e.g. text), embed all labels you want to consider -> produces an embedding x_text/x_label
        - text = "a photo of a (<object name>)"
        - x_text/label
      - embedd image -> produces an embedding x_img
        - x_img
      - label = classification = max( comparison(x_text, x_img) )
        - produce the label that is most similar btw the embedding image given and all the texts (with the label)
    - this halfs the distance to y = x! i.e. really robust
    - Q: does it mean anything to do this in reverse? 
A3: first one tells you which text/label is most similar to the query image. The second which text is most similar to 
the text. So it choose an image closest (from a set) to a given text. Is this interesting?

#

Hi everyone,
We will be hosting our fifth guest speaker, Ludwig Schmidt (University of Washington, LAION), today from 3:30-4:20PM. The talk can be found at the following link:
https://www.youtube.com/watch?v=brHeIKX8ayw

If you have questions during the talk, please post them to the speaker-questions channel in the discord.

Remember to fill in your attendance forms after the talk. The form is due by EOD on 2/1

Helpful Reading Materials for the Talk:

- https://arxiv.org/abs/2103.00020 , specifically the robustness evaluation in Section 3.3
- https://arxiv.org/abs/2109.01903 
- https://arxiv.org/abs/2205.01397 

Talk Details

Title: A data-centric view on reliable generalization
Abstract: Researchers have proposed many methods to make neural networks more reliable under distribution shift, yet there is still large room for improvement. Are better training algorithms or training data the more promising way forward? In this talk, we study this question in the context of computer vision and OpenAI’s CLIP model for learning from image-text data.First, we survey the current robustness landscape based on a large-scale experimental study involving more than 200 different models and test conditions. The CLIP models stand out with unprecedented robustness gains on multiple challenging distribution shifts. To further improve CLIP, we then introduce new methods for reliably fine-tuning models by interpolating the weights of multiple models. Finally, we investigate the cause of CLIP’s robustness via controlled experiments to disentangle the influence of language supervision and training distribution. While CLIP leveraged large scale language supervision for the first time, its robustness actually comes from the pre-training dataset.

Based on our findings, we will conclude with initial experiments to improve the pre-training datasets for image-text models. 

----

I think we should have scribes that jot down the questions from discord and then answer them based on the discussion section. Add that to 5% attendance 5% scribe of discussion questions, ppl only need to scribe once and groups of 2-3 should be very doable.