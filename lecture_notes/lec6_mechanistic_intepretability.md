# Lec - Mechanistic Interpretability – Reverse Engineering Learned Algorithms from Transformers
Stella Biderman (EleutherAI, Booz Allen Hamilton)

attendance: https://forms.gle/Qow74t8tK4UbMyqV8
webpage: https://stanford-cs324.github.io/winter2023/
canvas: https://canvas.stanford.edu/courses/169201

## Summary
- 2 sentence summary 
  - 

Abstract:
Abstract: Transformers are exceptionally powerful technologies that have quickly gone from smashing NLP benchmarks to 
being one of, if not the premier ML technology in a wide array of fields. Given their growing role in technological 
pipelines and society at large, understanding how and why they work is a pressing issue. In this talk I give an 
overview of research on Mechanistic Interpretability, a field of work that has had substantial success picking apart 
transformers and understanding the algorithms that trained models use to reason. Topics covered include: the algorithm 
that toy LLMs can use to perform arithmetic accurately; how real-world LLMs do object identification; and how AlphaFold 
learns 2D projections of structures and then inflates them over time. Time permitting, I hope to discuss recent \
discoveries at EleutherAI currently under review for publication.

Paper: 

My summary of the abstract:

FMs summary:

Copypaste summary:

Main contributions:

refs:
  - https://www.lesswrong.com/posts/AcKRB8wDpdaN6v6ru/interpreting-gpt-the-logit-lens
  - https://ptb.discord.com/channels/1062159697819476048/1062434757033611374/1069664030702194698

## Notes

- misc info:
  - Mechanistic Interpretability – Reverse Engineering Learned Algorithms from Transformers
Stella Biderman (EleutherAI, Booz Allen Hamilton)
  - alpha fold is a transformer model.
  - Who we are. EleutherAI (/iˈluθər eɪ. aɪ/) is a decentralized collective of volunteer researchers, engineers, and 
  developers focused on AI alignment, scaling, and open source AI research.
  - Given their growing role in technological 
  pipelines and society at large, understanding how and why they work is a pressing issue
    - questionable! you need to justify this. Very well.
  - Davincci: https://learn.microsoft.com/en-us/azure/cognitive-services/openai/concepts/models
    - Davinci is the most capable model and can perform any task the other models can perform, often with less 
    instruction. For applications requiring deep understanding of the content, like summarization for a specific 
    audience and creative content generation, Davinci produces the best results. The increased capabilities provided 
    by Davinci require more compute resources, so Davinci costs more and isn't as fast as other models.

# Question

Q1:is it true that OPT-175B doesn't have emergent abilities (e.g. ICL) like the original GPT3 one does? Or is this just a rumor? 
A1:  



## Discord summary

The talk can be found at: https://www.youtube.com/watch?v=P7sjVMtb5Sg

Helpful Reading Materials for the Talk:
https://transformer-circuits.pub/2021/framework/index.html (main takeaways: what circuits are, “privileged bases”)
https://www.lesswrong.com/posts/AcKRB8wDpdaN6v6ru/interpreting-gpt-the-logit-lens
https://transformer-circuits.pub/2022/mech-interp-essay/index.html
https://transformer-circuits.pub/2022/toy_model/index.html (sections 1 though 4)

Talk details below!

Stella Biderman
Title: Mechanistic Interpretability – Reverse Engineering Learned Algorithms from Transformers
Abstract: Transformers are exceptionally powerful technologies that have quickly gone from smashing NLP benchmarks to being one of, if not the premier ML technology in a wide array of fields. Given their growing role in technological pipelines and society writ large, understanding how and why they work is a pressing issue. In this talk I give an overview of research on Mechanistic Interpretability, a field of work that has had substantial success picking apart transformers and understanding the algorithms that trained models use to reason. Topics covered include: the algorithm that toy LLMs can use to perform arithmetic accurately; how real-world LLMs do object identification; and how AlphaFold learns 2D projections of structures and then inflates them over time. Time permitting, I hope to discuss recent discoveries at EleutherAI currently under review for publication.
