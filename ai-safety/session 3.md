# AI Safety Fundamentals: Session 3 - RLHF: Reinforcement Learning From Human, or AI, Feedback

[toc]

------

## Focus

- *Explain how reinforcement learning from human feedback (RLHF) can be used to make models more helpful, harmless and honest.*
- <u>Describe challenges with RLHF</u>, including sycophancy, deception, undesirable preferences, difficulty with complex tasks, over- and under-censoring. <u>Evaluate the promise of RLHF approaches.</u>
- Explain the ‘**Constitutional AI**’ approach being by pursued by Anthropic, and its similarities and differences to RLHF.

## Readings

*Concepts that need further research to understand are ==highlighted in yellow==*.

### [The True Story of How GPT-2 Became Maximally Lewd](https://www.youtube.com/watch?v=qV_rOlHjvvs) 

- Good example of outer misalignment "where the AI has learnt something you didn't intend it to because you set your objective function incorrectly" - in this case it was the result of a simple bug inverting a component in the objective function.
- The explanation of RLHF is very summary, and specifies the system design approach at Open AI for aligning GPT-2

### [Illustrating Reinforcement Learning from Human Feedback (RLHF)](https://huggingface.co/blog/rlhf)

- RLHF is an attempt to improve upon and mitigate the shortcomings of simplistic objective functions such as `cross-entropy` loss on the next word prediction, or measures such as `BLEU` or `ROUGE` to evaluate model performance post training. It is intended to be used both for optimising as a feed-in to the objective function for computing loss and as a means of model evaluation post training.
- RLHF works by first getting a language model to produce outputs and then getting a human to evaluate these on a desirability scale, or by getting them to rank candidate outputs a model has produced. This is then fed back to the model as a signal for it to optimise for the more desired outputs or to down or up weight particular output types.
- RLHF has multiple component models which are used in combination to align the original language according to human's preferences. One of the main components is a **Reward Model** which takes in a sequence of text and returns a *scalar value* of how preferable that sequence of text, which constitutes an output of the original language model for a particular prompt, is. The Reward Model is trained on a dataset of prompts and human ranked outputs for that prompt - where the human ranks a set of a language model's produced outputs for the prompt, or similar ways of scoring outputs. The Reward Models are themselves language models which have the capacity to interpret text, as that is necessary for them to effectively correlate the rankings to types of outputs for a prompt -  the difference is they are designed so as to produce desirability scores for their outputs, not outputs themselves, you can imagine this as an additional layer on top of any text they produce as output which then runs it through a set of weights to produce a ranking between them, or something along these lines.
  - ![image-20240325143556105](../../assets/typora_images/image-20240325143556105.png)
- We now have both the original LM we want to align and an RM for producing desirability scores for it's output - via. training on human ranked prompt and sets of output pairs. Our goal then becomes trying to finetune i.e. align the original LM. This is usually done by making a copy of it and finetuning its parameters using **Proximal Policy Optimisation** which is a ==policy-gradient RL algorithm==. 
  - The problem formulation for this training paradigm is as such (==the underlined terms are from the RL literature==) - the <u>policy</u> is an LM that takes a prompt and returns a sequence of text, the <u>action space</u> is all the tokens comprising the LM's vocabulary, & the <u>observation space</u> is the distribution of possible input token sequences (dimension of `vocabulary size * length of input token sequence`). The <u>reward function</u> combines the preference model (RM) and a constraint on <u>policy shift</u>.
  - The <u>reward function</u> combines all the previously mentioned models, the original LM and the RM aka the preference model. Given a prompt the LM produces an output, concatenated with the prompt produced for, the output is passed to the RM to score, the score could be called $r_\theta$. The difference between the per token output probability distributions of the LM & RM are computed via. KL-Divergence, this could be called $\lambda{r_{KL}}$​. The objective function to optimise for is $r = r_\theta -\lambda{r_{KL}}$, which is sent to the RL update rule.
  -  This KL-Divergence term is used so that the LM is constrained to produce output that are *sensible* in order to prohibit it from producing output that might game the reward function but be incoherent. Intuitively, the RM being a language model itself is trained to produce sensible output and to weight the likelihood of such output highly, and so by requiring that the LM's output probabilities be close to the RM's for a particular prompt we prevent cases where it could optimise for $r_\theta$ whilst creating nonsense that diverges from it's initial coherence, which the RM possesses too, and thus magnifying the $\lambda{r_{KL}}$ term. Instead our reward function that combines these two by subtracting the latter from the former, ensures that the latter is minimised as well whilst the former is maximised.

### [Open Problems and Fundamental Limitations of Reinforcement Learning from Human Feedback](https://arxiv.org/pdf/2307.15217.pdf)

- Challenges with Obtaining Human Feedback
  -  Misaligned Humans: Evaluators may Pursue the Wrong Goals
    - Tractable: Selecting representative humans and getting them to provide quality feedback is difficult.
      - Political bias has been found to increase after RLHF, perhaps due to humans encoding their biases in their rankings
      - Finding representative human annotators for the particular alignment use-case is tricky
    - Tractable: Some evaluators have harmful biases and opinions. 
      - Humans have some negative ideas etc.
    - Tractable: Individual human evaluators can poison data.
      - Humans can be compromised to try and subvert the alignment intention of the RLHF exercise, since the RLHF data for training reward models is collected from human annotations, this is a problem if they have alternate motives etc.
  - Good Oversight is Difficult

### [Constitutional AI: Harmlessness from AI Feedback](https://arxiv.org/pdf/2212.08073.pdf)

- ![image-20240325154420314](../../assets/typora_images/image-20240325154420314.png)
- I get the impression the approach works like this. 
  - **Phase 1:** get a model that is trained to be helpful to give responses to harmful prompts (e.g. asking for instructions on carrying out crimes etc.) and since it is a helpful model it will help with harmful requests and thus be harmful itself. Then take those responses, and sampling from a set of your own **constitutional principles** (which are perhaps 'dictates' or pithy phrases of ethics to guide behaviour, like the ten commandments etc.), provide said principles as grounding prompts by which the model is asked to critique it's original harmful response. Keep doing this by randomly sampling from your principles and after generating many critiques, pass these critiques as context prompts for the AI to align itself with i.e. to revise it's initial response in light of. In summary - get helpful AI to generate helpful response to harmful prompt thus meaning it has a harmful response, then get AI to critique its harmful response according to your principles, and then get AI to revise its harmful response according to its own critique.
  - **Phase 2:** this is a mimicking of RLHF but instead of a human we use the AI's feedback, so it is RLAIF. Like the Reward Model in RLHF is generated from human rankings, in this case the PM (preference and reward model are interchangeable it seems), is trained on the set of constitutional principles we have set, via. the resultant revisions the AI has made to its own initial responses. The AI trained to revise as such is then used again to generate responses to harmful prompts, the prompts and the AI's responses are then grouped into pairs of prompt and multiple responses. These form the basis of a dataset structured as a multiple choice question task, where the question asked is for this prompt, which response is best according a constitutional principle. As a result we then receive AI generated rankings of its own responses, after the AI has already self-trained itself to align with a set of constitutional principles. This ranked dataset is used to train another model i.e. the PM (the model which revises itself is the original LM) which is used to guide the original LM via. feedback and using RL to update its responses.
  - So it seems like this is essentially self-reinforcement using double layered constitutional principle alignment, first getting the AI to revise its harmful responses producing a more aligned LM, then getting that more aligned model to produce responses and evaluate between its now somewhat censored responses to rank its responses. Then on this dataset, we train another model, the PM, to produce scores for response desirability, and then employ this PM to direct the original LM according to RL update rules for aligning its outputs.



## Exercises



## Thoughts



## Resources

- [How to train a pretrained language model - a Hugging Face guide](https://huggingface.co/blog/how-to-train)
- [Instruct-GPT](https://openai.com/blog/instruction-following/)
- [Anthropic Reward Model Data Set](https://huggingface.co/datasets/Anthropic/hh-rlhf)
- [LoRA](https://arxiv.org/abs/2106.09685)
- <u>PPO - Proximal Policy Optimisation</u> - [[1]](https://huggingface.co/blog/deep-rl-ppo), [[2]](https://spinningup.openai.com/en/latest/algorithms/ppo.html)