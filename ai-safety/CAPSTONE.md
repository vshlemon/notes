# AI Safety Fundamentals: Final Project

> My project will focus on "model steering via. control vectors, also known as activation or representation engineering"

[toc]

------

# Readings

## [Function Vectors in Language Models](https://functions.baulab.info) by Eric Todd et al.

[Arxiv Paper](https://arxiv.org/pdf/2310.15213.pdf)

- In section 2.3:
  - They restrict their analysis to attention heads. Is this well motivated conceptually - I suppose attention heads state what parts of the input to focus on for a task, so it could be. But what if you sought to derive function vectors from the MLP layers of the residual blocks - isn't that potentially more potent since it learns on data of all the attentioned interactions?