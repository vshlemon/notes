# AI Safety Fundamentals: Session 5 - Mechanistic Interpretability

[toc]

------

# Focus

**How might we understand what’s going on inside an AI model?**

As modern AI systems grow more capable, there is an increasing need to make their internal reasoning and decision making more interpretable and transparent. This week we'll look at how people are analysing models' learned representations and weights through methods like circuit analysis, and teasing apart behaviours like superposition with dictionary learning. The final resource looks at performing circuit analysis, identifying a circuit for indirect object identification in GPT-2.

**By the end of the session, you should be able to:**

- Understand what mechanistic interpretability is, and how it could help with the AI Alignment problem
- Understand key mechanistic interpretability concepts, including circuits and superposition.

# Readings

## [**What is mechanistic interpretability?**](https://www.youtube.com/watch?v=sISodZSxNvc) by Neel Nanda and Daniel Filan (2023)

> Neel Nanda briefly explains what mechanistic interpretability is, and his motivations for studying it.



## [**Zoom In: An Introduction to Circuits**](https://distill.pub/2020/circuits/zoom-in/) by Chris Olah, Nick Cammarata, Ludwig Schubert et al. (2020)

> This paper introduces the "circuits" perspective on analyzing neural networks, which involves explaining neural network behaviour in terms of features and circuits that connect them.
>
> While reading, keep the three claims about neural networks near the beginning in mind, evaluating whether you think the evidence in the paper supports them.

- <u>Claim 1: Features:</u> *Features are the fundamental unit of neural networks. They correspond to directions. These features can be rigorously studied and understood.*
  - They take neural networks to consist of meaningful, understandable features. For example earlier layers in vision models could be taken to represent more basic fundamental constructs such as edge or curve detectors, and later layers could be taken to represent things like wheel detectors or floppy ear detectors - depending on the data the model was trained on.
  - **Example 1: Curve Detectors:** They identify curve detecting neurons in every non-trivial vision model. For InceptionV1's early layer denoted `mixed3b` they find the units to respond to curved lines and boundaries with a radius of 60 pixels, and see them as easily excited by perpendicular lines along the boundary of the curve, and when two sides of the curve are of different colours. Reasons for why they believe these units to be curve detectors are given below.
    - <u>Argument 1: Feature Visualisation</u> - *by tweaking the input values via. backpropagated optimisation to get the curve detecting units to fire more they reliably produce altered input images with more well defined curves in the expected orientation - I assume they set the curved units to high activation values and backpropagate to update the values of the input to optimise for producing such activations as their outputs at the layer in question*
    - <u>Argument 2: Dataset Examples</u> - *they note that the images that get these neurons to fire more with higher activations are those that quite clearly have very well defined curves in them of the expected orientation, and those that get them to fire moderately are most often those with less well defined curves, or curves that are somewhat off the expected orientation they take the neuron to be highly activated by - thus indicating the firing is produced reliably by well defined curves in a particular orientation*
    - <u>Argument 3: Synthetic Examples</u> - *similar to the above argument, when artificially generating synthetic images of curves with varying orientations, curvatures and so forth the activations only fire strongly for curves in the expected orientation and with the significant amount of definition, and do not fire as strongly for other orientations and definition levels*
    - <u>Argument 4: Joint Tuning</u> - *by taking dataset examples and gradually rotating them, when passing them in as inputs the units tuned for a certain orientation slowly stop firing and instead units tuned to another orientation begin firing - this indicates that there are different units that are tuned for detecting rotated versions of the same thing, spanning the 360 degrees of all potential orientations*
    - <u>Argument 5: Feature Implementation</u> - *they presume that by inspecting the circuit implementing the curve detectors they can read a curve detection algorithm off the weights - they don't believe there is a secondary reason for the firing of these particular units in a presumed circuit*
    - <u>Argument 6: Feature Use</u> - *the downstream clients i.e. later layers, of the curve detectors are those that appear to represent features naturally involving curves e.g. circles, spirals etc.*
    - <u>Argument 7: Handwritten Circuits</u> - *taking their understanding of how curve detectors are implemented they can recreate an equivalent functionality by hand setting the weights - which indicates that the particular weight settings in the presumed circuits with respect to the input form a reproducible curve detection algorithm*
- <u>Claim 2: Circuits:</u> *Features are connected by weights, forming circuits. These circuits can also be rigorously studied and understood.*
- <u>Claim 3: Universality:</u> *Analogous features and circuits form across models and tasks.*

## [**Toy models of superposition**](https://transformer-circuits.pub/2022/toy_model/index.html) by Nelson Elhage, Tristan Hume, Catherine Olsson et al. (2022)

> This work explores "superposition" in language models - the phenomenon where neural networks represent more features than they have dimensions. It performs empirical research on toy models to gain insight into how superposition might work in larger models. Superposition poses a challenge for mechanistic interpretability, because it makes internal representations much more complex to understand.
>
> While reading, try to write down your own definitions for the key terms used in the paper.
>
> For those less familiar with linear algebra, [this video](https://www.youtube.com/watch?v=fNk_zzaMoSs) offers an introduction to vectors. For a different presentation of the information, [this video](https://www.youtube.com/watch?v=R3nbXgMnVqQ) walks through the paper with an interpretability researcher.

- **Superposition** *is when models represent more features than they have dimensions*
  - As features become more sparse (for e.g. empty values at the feature index) the model uses more dimensions to represent the features. If you have an embedding of 5 features represented by 2D vectors and you make more of them sparse the model learns to use more dimensions to represent them, whereas if you make them more dense i.e. more of the 2D vectors have values then the model uses less dimensions to represent them. This is likely due to the features being more easily distinguishable when denser as the information in them is more compact and thus a lesser number of orthogonal dimensions like in PCA can be used to distinguish them, whereas with sparser features there is less information and so more dimensions are needed to distinguish them. *This can lead to the idea that smaller models trained on more dense features can represent them in less dimensions and thus mimic larger models trained on more sparse features which require more dimensions to represent them.* <u>A sparse structure in superposition can be understood as requiring less dimensions to represent more features.</u>
  - **Monosemantic** means when a neuron responds to a single feature - <u>however it is not obvious to me what feature means here - is a single embedding vector e.g. for representing a word, or can it be a group of input indexes in an image corresponding to a humanly understandable notion e.g. a circle or line or eye etc.</u>
  - **Decomposability** is where network representations can be described in terms of independently understandable features
  - **Linearity** means that features can be represented by direction, <u>however what this really means is not clear to me, but I presume it indicates that the direction of activation of a neuron dependent on input is what represents a feature</u>*
  - **Privileged Basis:** Only some representations have a *privileged basis* which encourages features to align with basis directions (i.e. to correspond to neurons).
  - **Superposition:** Linear representations can represent more features than dimensions, using a strategy we call *superposition*. This can be seen as neural networks *simulating larger networks*. This pushes features *away* from corresponding to neurons.
- *Motivations for the work on superposition by Anthropic*
  - **Word Embeddings**
  - **Latent Spaces**
  - **Interpretable Neurons**
  - **Universality**
  - **Polysemantic Neurons**
- *What are features?*
  - <u>Feature</u> is, at a high level, being used to denote the interpretable (humanly?) properties of the input (image, text etc.) that we can observe neurons as responding to
  - *Features as arbitrary functions:* this would define features as <u>any</u> function of the input. But it doesn't seem accurate as the features being observed seem to be fundamental abstractions of concepts and building blocks of meaning within the data. In addition these seem to form reliably across models (such as curve detectors for vision models) indicating something more concrete and consistent than a simply arbitrary function. Features also are identifiable and can be matched to human notions - for example we can identify `cats` and `cars` indicating there is no arbitrariness, and non-related concepts often don't combine in meaningful ways like related concepts learnt by features do such as `queen-man` etc. which incorporates fundamental concepts like gender.
  - *Features as interpretable properties:* features are usually understandable to humans and match their concepts, as mentioned above.
  - *Neurons in sufficiently large models:* another definition could be features are properties of the input which a sufficiently large neural network would reliably dedicate a neuron to representing.
- *Features as Directions*
- *Privileges vs. Non-Privileged Bases*
- *The Superposition Hypothesis*

## [**Towards Monosemanticity: Decomposing Language Models With Dictionary Learning**](https://transformer-circuits.pub/2023/monosemantic-features/index.html) by Trenton Bricken, Adly Templeton, Joshua Batson et al. (2023)

> This paper attempts to address the challenge of superposition raised in the previous one. The authors demonstrate that dictionary learning via sparse autoencoders can decompose language model representations into more interpretable features.

- **Polysemanticity** is when one neuron represents a number of different features i.e. is activated or responds to many different input types & the concepts in them e.g. a single neuron in a language model was found to respond to a mixture of academic citations, English dialogue, HTTP requests and Korean text. Thus while there may be some underlying complicated reasoning for this mixture of concepts a single neuron responds to - such as their statistical association, or the training data order in which the model learnt, or maybe some non-humanly understandable notion that underlies them all - the concepts learnt are too multifarious or diverse in terms of human significance.

# Exercises

## Do the speculative circuits claims hold up?

This is a brief [writing-to-learn exercise](https://docs.google.com/document/d/1ADDu8qF0cdJPj-lboOesdTYW822gMfkr2NQ-7tjgxjM/edit), expected to be no more than half a page. It is intended to be less intensive than previous exercises given the intensity of reading this week.

Pick one of [the three claims](https://distill.pub/2020/circuits/zoom-in/#three-speculative-claims:~:text=Three Speculative Claims about Neural Networks) (features, circuits and universality) given in the circuits paper. Then:

1. Summarise what the claim is in your own words. Explain if you think you might be uncertain what the claim is.
2. What evidence or arguments support and reject the claim? (this can be from the circuits paper itself, the other resources, or other information you find)

## (Optional) Comprehension Questions

These questions should be answerable using only the core resources above. Write your answers to the following questions in the box below.

### <u>Zoom In: An Introduction to Circuits</u>

1. What are the three key claims about neural networks that the paper introduces and evaluates?
2. How do features and circuits relate?
3. What does it mean to say a feature is a "direction" in a neural network?
4. What are some examples of circuits or features identified in the paper?
5. What evidence is there that image models detect features like curves?
6. What is a polysemantic neuron?
7. Why do polysemantic neurons make interpreting models more difficult?
8. Suggest a possible circuit that might be present in a large language model.

### <u>Toy Models of *Superposition*</u> 

9. What is "superposition" in neural networks?
10. What does the "sparsity" of features mean?
11. Why is high sparsity likely in practice with large language models?
12. More superposition tends to occur if features are _____ [less/more] sparse.
13. Why might disentangling superposition help us interpret neural networks?
14. What were the three strategies to resolving superposition suggested in the 'Toy Models of Superposition' paper?

### <u>Towards *Monosemanticity*</u>

15. What type of neural network or algorithm did Anthropic show helped perform dictionary learning to identify learned features in a model?
16. Explain the general approach taken in the 'towards *Monosemanticity*' paper.
17. Explain what [feature #442](https://transformer-circuits.pub/2023/monosemantic-features/vis/a1.html#feature-442) is in A/1, and suggest a way we could use it.

### <u>Interpretability in the Wild (from the further resources)</u>

18. What specific capability in GPT-2 small does this paper analyze?
19. Describe the algorithm the paper proposes GPT-2 is carrying out to perform this task.
20. What are the three major classes of token heads the paper claims implement this algorithm?
21. What is path patching? How did this help the authors identify the relevant heads?

*You can check your answers against [the answer key](https://docs.google.com/document/d/1hEfb-gvvyfyPtBLwqy8v2BBUCCBPACc4a3rxhD29A8k/edit).*

# Thoughts

