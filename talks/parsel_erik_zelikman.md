# Talk - Parsel

## Summary
- 2 sentence summary
  - 
  - 

Paper Abstract:

My summary/FMs summary:

Motivation/problem being solved:
- LLMs are bad at generating programs when there are chains/compositions in one shot

Main contributions:

refs:
- https://github.com/ezelikman/parsel

## Notes

misc info:
- nodes: a required implementatin of a program
- sometimes we have asserts/tests for each node
- child part of the parent strongly connected components
- treat a function without asserts as depeding on its parents
- solve them together
- you hope that sampling via decomposition increases the chances the right program
- algorithm:
  - sample at the bottom up
  - make sure all the tests are passed then you do bottom up
- putting together function
  - treat subfunction fixed
- Eric leverages that fact LLMs are good at "planning" (his version of planning = breakin down, 
but thats not what Seb said, Seb suggests some sort of memory I think)
  - i.e. break a problem into sub steps
- parsel = NL + indentation
  - NL1 -> ?
    - NL2 -> function
    - NL3 -> function
- for each NL description, put def for it and then the NL is the comment to it +
  - the top level function receives from ... import implementations for NL2, NL3 etc. and as a comment the NLi to describe what it does
- hargest part for Parsel/LLMs
  - think the step by step part
    - Q:why?
    - the comment as description (desc) is important to avoid specifying/testing combinatorially all the implementations
    - possible, but instead the top level just knows what it does via NL description
- Experiments
  - APPS pass rate
  - (vs code force?)
- 1x8 = 1 program and 8 implementation
- Test Gen ~ CodeT


# Question

Q1: How are the graphs generated? Does the LLM generate it?
A1: 

Q2: Why not automatic test generation?
A2:

Q3:  Limitations to Theorem Proving (TP)? 
A3:

Q4: What about if the decomposition is not correct? do you do backtracking?
A4: 

Q5: How do you know your decomposition is correct?
A5: it's to know if you are wrong cuz you don't know if you've sampled enough.

Q6: Why can't you do this with GPT-4 naively?
A6: 

Q7: Why is the think by step by step the hardest?
A7: 

Q8: langchain vs Parsel?
A8: 

Q9: How do you generate parsel programs? what is input to output parsel?
is it LLM(original_problem, solve it via parsel step by step)
A9: 

Q10: How to remove the exponentiation in parsel? Is it even worth removing?
A10: 

# Speaker Bio

Origina:

Summary:

Mu Summary: