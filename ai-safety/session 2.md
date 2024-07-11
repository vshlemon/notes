# AI Safety Fundamentals: Session 2 - What is AI Safety?

[toc]

------

## Focus

- Describe the key areas of AI safety, including alignment, moral philosophy, competence, and governance
- Understand how some people have classified some types of alignment failures (outer vs inner alignment, sycophants vs schemers)

------

## Readings

### What is AI Alignment - Adam Jones [Article]

- Glossary

  - Alignment: making AI systems do as intended

    - > Summary: 
      >
      > Outer - ""
      > Inner - "AI does what you ask but not what you intend"

  - Moral Philosophy: determining 'good' intentions to instil in AI

  - Competence: developing AI capable of doing as intended

  - Governance: deterring harmful development of AI systems

  - Resilience: preparing other systems (socioeconomic etc.) to cope with changes to life from AI

  - Security: preventing the AI systems themselves from attack

- **Outer Alignment** - to mitigate situations where the reward function you specify is:
  - a1) well defined but permits also optimising for outcomes you didn't intend (eg. optimise for user engagement but then has also encouraged optimising for clickbait, extremist content etc. which you didn't intend it)
  - a2) ill defined regards the outcome you wished to see i.e. a poor proxy (eg. optimise for llm truthfulness by using a reward function to mimic how humans rate answers, but given how llms learn to emptily mimic they end up producing correct sounding but false answers)
    - the question is what should be the right way to represent the outcome in a data-structured learning task, mimicking human preference is probably insufficient since llms are just statistical regurgitators and don't encode meaning. for these kinds of things there must be some reference fact to ensure truthfulness to it, which requires a reference methodology to compare against. e.g. proofs in mathematics can be correct or not due to the logical steps, language is more fuzzy - and needs clarification of terms and reference encoded to the states they refer to.
  - b) the agent learns to optimise it with the right intents (behaviours and patterns of approaching the problem you would have intended for it to develop)
- **Inner Alignment**
- I honestly don't see much difference between the two forms of alignment, but my understanding is that outer alignment is about the reward function not matching the designers intended outcome, whereas the inner alignment issue is about the system not learning to replicate the intended behaviour despite the reward function being correctly designed for intended outcome. However in both cases, the outcomes are prone to be what was not intended, and in both cases it is the designers fault. In the outer case they haven't mitigated how optimising for their reward could also optimise for other anti-reward states, in the inner case the training environment reward could have been optimised by the agent in some strange manner which leads to behaviour in the outside world resulting in unintended outcomes.



### Intro to AI Safety - Robert Miles [Video]



### [Why AI Alignment Could be Hard with Modern Deep Learning - Ayeja Cotra [Blog]](https://www.cold-takes.com/why-ai-alignment-could-be-hard-with-modern-deep-learning/)

- AI can often develop motivations & methodologies for achieving outcomes that were not intended by the designer. It is hard to ensure a particular method or motivation is developed before-hand when using deep-learning models as the model effectively learns how to optimise for the objective/reward function by searching for a program to do so - as opposed to traditional software where the program i.e. recipes of steps are explicitly instructed by the designer. This is a search carried out across a vast number of parameters and it is hard to interpret let alone direct, additionally since the meaning of particular parameters and circuits of them only emerges in conjunction with the model and its learning task, there is no predicate of what a parameter or circuit will come to mean & the same architecture trained on the same data-set could potentially form very different circuits dependent on the training experience - eg. the shuffling and order of the data examples to train on, or the parameter initialisation states etc.
- ...
  - **Saints** -- people who genuinely just want to help you manage your estate well and look out for your long-term interests.
  - **Sycophants** -- people who just want to do whatever it takes to make you short-term happy or satisfy the letter of your instructions regardless of long-term consequences.
  - **Schemers** -- people with their own agendas who want to get access to your company and all its wealth and power so they can use it however they want.

### [Goal Mis-generalisation: Why Correct Specifications Aren’t Enough For Correct Goals - Deep Mind Team [Blog]](https://deepmindsafetyresearch.medium.com/goal-misgeneralisation-why-correct-specifications-arent-enough-for-correct-goals-cf96ebc60924)

- Even if your reward is well specified your agent can learn to achieve it in ways which whilst optimal during training are suboptimal at test time when deploying to the real world environment. This can be due to the training and test environments differing and the agent having learnt a strategy at training that was not intended. This means great attention needs to be paid into thinking about the environment, what the agent might learn, how it might optimise reward through ancillary means to the behaviour it is intended to learn, and how to ensure it learns that behaviour instead.
- 





------

## Exercises

### Identifying Uncertainties

Spend ~30 minutes answering the question: **What are my key uncertainties about AI safety and the alignment problem?**

You might want to consider:

- Are there any 'obvious' potential solutions to AI safety that come to mind? (We'd encourage brainstorming a long list first, before trying to argue about them)
  - Stop developing AI
  - Focus efforts on equitable human sustenance, and societies that ensure baseline well-being for all humans in balance with the earth's resources
  - Stop the continual 'progress' oriented mindset
  - Stem satiation of intellectual curiosity and worldly facility through development of technologies
  - Have regulation on what types of technologies are worked on and why, requiring government approval **before** research begins
  - Require consent for using data in training AI models
  - Impose prohibitive regulation around data collection in real world using perceptual systems (cameras, microphones etc.)
  - Make all AI projects pass an "ethical studies" criteria which outlines/establishes alignment criteria for proceeding with research
  - Give certification to use of commercial AI systems for safety of use - after passing extensive testing/red-teaming
  - Require inter-governmental (COP, UN, NATO style boards) agreement for use-cases/applications of AI research and what falls outside it
- How likely do you think it is that human-level machine intelligence arises in the next 10 years? What about 100 years?
  - Tricky to say what 'human level' means, if it means abstract reasoning and not just pattern replication/mimicking but some other level of identifying logic then that should be feasible once the methodologies for following logic in different human fields can be encoded into instructions in the form of model architecture (eg. how chess/go reasoning can be simulated using decision trees).
  - Likely that AI will be intelligent - if intelligence means facility with manipulating an environment - in ways different to humans re the facilities/mechanisms, and perhaps exceeding them regarding extent of manipulation possible fairly soon, if they are not already given the scale at which they can perform processing on inputs - even if they are only 60% of our approx. capabilities they can perform to that level on exponentially larger inputs which opens scope for them to be more impactful in exercising their intelligence, and perhaps if intelligence grows by number of inputs and examples and abstracting knowledge of relations between them then they will far exceed us very soon.
  - So I believe they are already ahead in a number of ways, may need extension to more logical reasoning areas, but are probably at the level where their impact can exceed us now - depending on deployment to particular applications and input environments.
- Do you think AI systems that we build will actually pursue convergent instrumental goals (mentioned at [13:16 in Intro to AI safety](https://www.youtube.com/watch?v=pYXy-A4siMw&t=796s))? Why and why not?
  - Didn't think about their world models containing us and them being stringently set on achieving their goals according to original instructions. Must be some mode of ensuring instructions of varying types are ordered in priority of command eg. listening to request to switching off overrides any other instruction
    - Self preservation - AI trying to stay alive
    - Goal preservation - AI always trying to complete task
    - Resource Acquisition - AI trying to extend itself by consuming greater resource
    - Self Improvement - AI trying to optimise its facility to impact
- Will AI systems be safe by default? Why and why not?
  - Don't think so, what does default mean? If you take the simplest thought experiment of building intelligent AI by training it to mimic humans then since humans are not safe in their behaviours it will not be. And if by default you mean at birth before any exposure to external world environments and culture, then humans could be said to be safe but then when introduced into complex environments with competitive cultures and ideologies they become unsafe, or when threatened with dangerous prospects they develop unsafe behaviours to protect themselves either intentionally 'bad' or because they have no idea of which other way to protect themselves etc. Individuation and the internal biological drive to self-protection can manifest in many harmful ways depending on the existing circumstances an agent is introduced to.
- What might be some real-world consequences of misalignment?
  - Existential threat through malicious AI - developing self oriented motivations for success at human's expense or with accompanied antagonism for a competing species/entities - or miscued AI that has developed strange mechanisms to achieve it's training reward but which doesn't succeed in real world (eg. a vehicular AI trained to get from A to B as fast as possible learns that roads are inefficient and so it finds ways to increase it's size and steamroll buildings and people etc.)
- Will we have one big AI system? Many copies of the same powerful AI? Lots of different AI systems?
  - No idea, most intelligent system might dominate and outperform others but also self-replicate
  - Or maybe many systems, of general applicability i.e. non specialised AI, might be competing for supremacy, might depend on order of magnitude difference of intelligence via. training data, resources (electricity, chips etc.) and architectures; if one so greatly outperforms the others likely to be one and a self-replicating one at that.
- Who's intentions or which "values" should we be aligning AI systems with? How would you handle different stakeholders wanting to align AI systems with different intentions or values?
  - Humans haven't agreed on 'values' for since the species emerged, unlikely to happen in a century, but then again survival pressures and attraction to comfort and safety has motivated grouping together (governments etc.) to preserve these for the larger number of us that are not competition oriented, but then those larger groupings end up becoming competition oriented either through falsely perceived threat or merely claim of apparent threat to them in order to veil an inclination to extend past baseline sustenance and comfort to being more rewarded/successful than others. We probably have some evolutionary mechanism that makes co-operation difficult unless prompted by fear, or psychologies that have developed towards making competition more likely etc. Unlikely to be disentangled any time soon. We all see others as separate entities meaning motivations differ at present at least, but some people are inclined towards protection of self and others towards extending their powers, if the former group's inclinations are incentivised then we could agree on motives for that end and ensure them.

In particular, if you're convinced one way on a particular topic, we'd encourage really digging into the opposite argument. 

### Misalignment Case Study

Answer the following:

1. What do you think the human-level intended outcome for the system was?
   1. To optimally balance the collection of keys for unlocking chests, and only collect keys for opening chests, not in and of themselves, and to do so efficiently
2. What was the goal specified to the model?
   1. Open chests
3. What did the model actually do?
   1. Collect keys - because in the training environment this resulted in a more frequent update (reinforcement) of its reward function (less sparse) as by getting many keys all at once - since there were less of them than chests - it then got a burst of reward as it could unlock all chests it encountered; if it didn't collect all keys it would often encounter chests it could not open and get no reinforcement or potentially a negative one. However because it learnt to collect keys, not just open chests efficiently, in the test environs where keys were more numerous it just went about collecting them even though there were way more than needed to open the chests
4. Is this outer or inner misalignment?
   1. Inner misalignment - AI agent learnt a weird way to optimise for the intended reward/outcome because the training and test environs were not properly aligned and curated to ensure what was learnt was intended, but also somewhat outer misalignment since guardrails were not placed to more effectively match intended behaviour within the reward function
5. Only if outer: What flaw in the reward signal is being exploited? Why does this achieve the goal specified, but not the human-level outcome?
6. Only if inner: What change in distribution occurred between training and deployment? (anthropomorphising the policy here) What learned goal does the model appear to pursue when deployed?
7. Does this failure have any traits that are similar to a scheming or sycophantic model? (the answer will be no for some case studies!)



------

## Thoughts

