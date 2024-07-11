# AI Safety Fundamentals: Session 7 - Contributing to AI Alignment

> A Guide to Careers & Projects in AI Alignment

------



[toc]

------

# Resources

## [**Become a person who Actually Does Things**](https://www.neelnanda.io/blog/become-a-person-who-actually-does-things) by Neel Nanda (2022)

> Motivation article on doing over planning

## [**Working in AI Alignment**](https://aisafetyfundamentals.com/blog/alignment-careers-guide?_gl=1*83607*_ga*MTIwMTIzNTY2OS4xNzA2MTg2OTk3*_ga_8W59C8ZY6T*MTcxMzg2ODg3NS40OC4xLjE3MTM4Njk3NjUuMC4wLjA.) by Charlie Rogers-Smith (2024)

> A career guide on the types of roles in the AI alignment field, and the temperaments, aptitudes and skillsets that are useful for them

<u>Relevant to me</u> *(essentially roles as a software engineer applied to ML research experimentation and product development)*:

- **Research Contributor (Experimentation)** & **Software Engineer (ML Systems & Toolkits)**: 

  - **Research Engineer** roles are usually available at industry orgs or similar nonprofits, such as DeepMind, OpenAI, Anthropic, and Redwood Research. You are expected to work on a team to execute on research projects proposed by others. *There is a strong component of understanding ML, especially at an applied practical level.* Software development skills and facility with different technologies is also key. 

    - > “As a rough test for the Research Engineer role, if you can reproduce a typical ML paper in a few hundred hours and your interests align with ours, we’re probably interested in interviewing you ([DeepMind](https://www.lesswrong.com/posts/nzmCvRvPm4xJuqztv/deepmind-is-hiring-for-the-scalable-alignment-and-alignment))”.

    - [A rough pathway - recommendations are to replicate papers, create demo notebooks investigating GPT's, explore and articulate the fundamentals of different techniques especially LLM's, Reinforcement Learning & Computer Vision etc.](https://forum.effectivealtruism.org/posts/7WXPkpqKGKewAymJf/how-to-pursue-a-career-in-technical-ai-alignment#How_to_pursue_research_contributor__ML_engineering__roles)

      - [MLAB](https://forum.effectivealtruism.org/posts/vvocfhQ7bcBR4FLBx/apply-to-the-second-iteration-of-the-ml-for-alignment) is a recommended applied ML/Alignment programme
      - [ARENA](https://mango-ambulance-93a.notion.site/ARENA-Virtual-Resources-7934b3cbcfbf4f249acac8842f887a99) run a very good course on AI alignment, interpretability & fundamentals (RL etc.). **Is the best first course to take.**
      - [Some rough guidelines on the basic background for ML research SW engineering](https://forum.effectivealtruism.org/posts/7WXPkpqKGKewAymJf/how-to-pursue-a-career-in-technical-ai-alignment#Machine_learning)

    - [This is an article by DeepMind who are hiring for Scalable Alignment focussed engineers which is a pathway more geared towards specifically technical alignment work rather than a broader sense of ML engineering](https://www.lesswrong.com/posts/nzmCvRvPm4xJuqztv/deepmind-is-hiring-for-the-scalable-alignment-and-alignment)

  - **Software Engineer** roles could be those working on <u>productionising ML solutions and building systems</u> around them e.g. for deploying models, designing the data architecture and model training aspects, orchestrating tasks and infrastructure, as well as building consumer applications and backend systems etc. Or could be <u>building ML toolkits and support libraries</u> e.g. like *Langchain* etc.

    - See some articles - [[1]](https://www.alignmentforum.org/posts/YDF7XhMThhNfHfim9/ai-safety-needs-great-engineers), [[2]](https://jobs.lever.co/Anthropic/436ca148-6440-460f-b2a2-3334d9b142a5) - on approaches to upskilling and gaining work - the main takeaway is work on a variety of projects to demonstrate your skills and make them visible in a portfolio, as well as contributing PR's to existing ML libraries and toolkits.
      -  e.g. work on productionising ML systems displaying backend skills as well as facility with distributed architecture and common infrastructure requirements etc. (think ZoomCamp or FullStackDL type things)
      - e.g. contribute a PR to *Langchain, LlamaIndex* etc.
    - A general software career transition guide for work on impactful problems with a section for work as a software engineer on AI Safety - [[1]](https://80000hours.org/career-reviews/software-engineering/) - & a more specific guide by a Google Brain staffer [[2]](https://80000hours.org/articles/ml-engineering-career-transition-guide/).  Roles in industry where you could work on AI & ML systems in general - infrastructure engineer, cyber security specialist, backend engineer, applications & systems developer etc.

## [**What we didn’t cover in this course**](https://aisafetyfundamentals.com/blog/not-covered-early-2024-alignment/?_gl=1*83607*_ga*MTIwMTIzNTY2OS4xNzA2MTg2OTk3*_ga_8W59C8ZY6T*MTcxMzg2ODg3NS40OC4xLjE3MTM4Njk3NjUuMC4wLjA.) by Adam Jones (2024)

> **Developmental Interpretability** - Is the study of how the structure of models changes as they are trained. Rather than features and circuits, the object of study is phases and phase transitions during the training process. This takes inspiration from developmental biology, which increased our understanding of biology by studying the key steps of how living organisms develop. [Read more](https://www.lesswrong.com/posts/TjaeCWvLZtEDAS5Ex/towards-developmental-interpretability).
>
> **Agent foundations** - Much of the course was focussed on neural network approaches, however it is not certain if future systems will continue to be built on this foundation. Agent foundations research is primarily theoretical research that aims to give us the building blocks to solve key problems in the field, particularly around how powerful agentic AI systems might behave. It draws a lot from maths, philosophy, and theoretical computer science, and in some ways is the [basic science](https://en.wikipedia.org/wiki/Basic_research) of alignment. [Read more](https://intelligence.org/files/TechnicalAgenda.pdf).
>
> **Adversarial Robustness** - Adversarial attacks on AI models exploit particular flaws or weaknesses in AI systems to cause them to fail, often by only [subtly tweaking inputs](https://medium.com/@ml.at.berkeley/tricking-neural-networks-create-your-own-adversarial-examples-a61eb7620fd8) or [using inputs that would be bizarre to humans](https://arxiv.org/pdf/2307.15043.pdf#page=28). This has serious implications for being able to [prevent misuse](https://www.alignmentforum.org/posts/timk6zHDTFdrHYLmu/adversarial-robustness-could-help-prevent-catastrophic). [Read more](https://far.ai/post/2023-03-safety-vulnerable-world/).
>
> **Shard theory** - Most people do not optimise some specific objective function all the time, but behave differently in different contexts: for example when their ‘hunger’ shard activates this might influence a decision to stop working and go for lunch, because this has worked well in the past (rather than because it optimises some complex objective function). Viewed through this lens, shards appear to result in models choosing actions over others in different situations, which indicates the model’s values. How shards develop therefore affects what values a model might also develop. Research in shard theory generally focuses on understanding the relationship between training processes and the resulting shards and learned values. [Read more](https://www.lesswrong.com/posts/8ccTZ9ZxpJrvnxt4F/shard-theory-in-nine-theses-a-distillation-and-critical).
>
> **Co-operative AI safety research** - We’ve previously seen instances of algorithmic systems interacting [in](https://www.technologyreview.com/2016/10/07/244656/algorithms-probably-caused-a-flash-crash-of-the-british-pound/) [undesirable](https://www.michaeleisen.org/blog/?p=358) [ways](https://en.wikipedia.org/wiki/2010_flash_crash), and [current AI systems seem to escalate conflicts when interacting with each other](https://arxiv.org/pdf/2401.03408.pdf). AI systems that are more capable and have control of more resources acting in undesirable ways might be a significant risk. Cooperative AI safety research (also called multi-agent safety research) explores how we might avoid or mitigate the impacts of these negative interactions. It also explores how we might encourage agents to coordinate in ways that result in positive outcomes. [Read more](https://arxiv.org/pdf/2012.08630.pdf).
>
> **Model organisms of misalignment** - We are already seeing [many AI risks](https://aisafetyfundamentals.com/blog/ai-risks/) starting to materialise. However, it’s still unclear how anticipated risks will emerge, particularly risks stemming from deceptive misalignment. This is where models appear to be aligned (possibly during training, or when they’re being carefully overseen by humans), but are actually misaligned and will pursue a different goal when deployed or not carefully supervised. Better understanding how and why deceptive misalignment occurs would help inform how we might prepare for these risks. It could also help better-inform policy decisions about AI safety, as well as decisions about what AI safety research to prioritise. Research into model organisms of misalignment seeks to achieve this by intentionally creating and then studying deceptively misaligned AI systems or subcomponents, in a controlled and safe way. [Read more](https://www.alignmentforum.org/posts/ChDH335ckdvpxXaXX/model-organisms-of-misalignment-the-case-for-a-new-pillar-of-1).
>
> **Technical moral philosophy** - We [briefly mentioned moral philosophy](https://aisafetyfundamentals.com/blog/what-is-ai-alignment/#:~:text=Moral philosophy%3A,hard to reconcile.) earlier on the course, which we described as determining intentions that would be “good” for AI systems to have. Technical moral philosophy research explores technical solutions or problems to identify good optimisation targets for advanced AI systems. Its more theoretical nature often means it overlaps with philosophy and agent foundations research. Recent work includes [Anthropic’s collective constitutional AI work](https://www.anthropic.com/news/collective-constitutional-ai-aligning-a-language-model-with-public-input), [OpenAI’s democratic inputs to AI program](https://openai.com/blog/democratic-inputs-to-ai-grant-program-update), and [the Meaning Alignment Institute’s work on moral graphs](https://meaningalignment.org/values-and-alignment-paper).
>
> **Alternative Training approaches** - [Imitation learning](https://ai.stanford.edu/blog/learning-to-imitate/) is an approach to training machine learning systems to copy humans. It is thought that this might result in better aligned AI systems because more capable systems might just copy humans better rather than get highly misaligned. It should be noted though that in some senses pre-training an LLM is imitation learning - to imitate what humans type on the internet - and this has not resulted in aligned AI systems [Inverse reinforcement learning](https://ai.stanford.edu/~ang/papers/icml00-irl.pdf) is an approach to machine learning that intends to infer an intended goal by observing human behaviour. This is similar to imitation learning but adds an extra step to infer the intended objective from the data (rather than matching the data being the objective itself).

## [**How to do an excellent AI alignment project**](https://aisafetyfundamentals.com/blog/alignment-project-guidance/?_gl=1*83607*_ga*MTIwMTIzNTY2OS4xNzA2MTg2OTk3*_ga_8W59C8ZY6T*MTcxMzg2ODg3NS40OC4xLjE3MTM4Njk3NjUuMC4wLjA.) by Adam Jones (2024)



## [**AI alignment project ideas**](https://aisafetyfundamentals.com/blog/alignment-project-ideas/) by Adam Jones (2024)



# Exercises

## Make your career awesome

During this course, you've learnt a lot about alignment, and you may now have a sense of the opportunities currently available. How might you factor this into your own career's big picture plan?

This exercise involves brainstorming different long-term paths you could pursue, similar to the suggestions by 80,000 Hours [here](https://80000hours.org/career-planning/process/longer-term-paths/). We encourage you to respond to the prompts below and list any uncertainties you have, and to submit your responses in the text box.

- What are 3-5 roles you could have in 5-10 years, that seem important for AI safety?
  - You could start by brainstorming roles you think are needed to make AI safety go well, then evaluate what roles currently exist and what jobs are [available](https://jobs.80000hours.org/?refinementList[tags_area][0]=AI safety %26 policy) (the available jobs does not necessarily reflect the work that needs to be done!)
  - You could also consider roles adjacent or related to AI safety, that would help with developing skills and relationships.
- Which of these roles would do you naturally feel most excited to test your fit for or work on?
- What [cheap tests](https://80000hours.org/career-guide/personal-fit/#do-cheap-tests-first) could help you actually test your fit for these different paths?

Optional other prompts:

- What strengths, skills, competencies, and other [career capital](https://80000hours.org/career-guide/career-capital/) do you already have? Set a [5 minute timer](https://www.google.com/search?q=5+minute+timer), and try to list at least 10 assets you have.

- What do you like and dislike about your current job? Have you had a past job you really enjoyed - if so, why do you think you enjoyed it?

- What goals did you write down in your icebreaker session? How can you now achieve them?

- Brainstorm other skills or areas of expertise that you could develop, that would enhance your ability to contribute. Try to focus on skills that are both 

  rare and valuable. 

  - Another framing for this is to have [sets of skills](https://www.lesswrong.com/posts/XvN2QQpKTuEzgkZHY/being-the-pareto-best-in-the-world) where very few people have capabilities in both, but that can be leveraged together in high-value ways. 
  - We encourage you to consider options that you'd be excited to explore, or have a comparative advantage for.

In your final session, you'll review your plan with your cohort peers. Come prepared with a brief explanation of your career plan in a format that you could share: for example a Google Doc or Word Online document.

## Make your project awesome

The project sprint is an opportunity for you to pursue your own self-directed project, that will help get you contributing to AI safety.

This exercise, in combination with [our project guidance](https://aisafetyfundamentals.com/blog/alignment-project-guidance/) will help you write up a brief project plan for your project.

To start with, let's generate some ideas (if you already have an idea, skip this):

- What goals are you trying to achieve by completing your project? Some ideas:
  - **Produce something that will enable you to demonstrate your skills to future employers**
  - [Master a relevant skill](https://www.scotthyoung.com/blog/2020/04/01/skills-that-matter/) so that you're better prepared in current or future roles
  - **[Develop your own hypotheses](https://www.cold-takes.com/learning-by-writing/) about important questions relevant to the alignment problem or specific research agendas**
  - Advance the field of AI safety by creating novel and important research
  - **Build a public portfolio of work by creating high-quality AI content**
- What research areas or paths to impact seem most exciting to you, or do you think you'll be most intrinsically motivated to work on? What draws you to these areas?
- What are your questions do you have in these areas you think are interesting and you don't currently have the answer to? Set a [5 minute timer](https://www.google.com/search?q=5+minute+timer) to think this through.
- What existing work can you find on these questions? If you find your answer quickly and easily, consider returning to the last prompt to generate new questions (you'll often find 'further work' sections in these papers though - suggesting what you might do next!).
- What are three ways you could find answers to these questions? What's the most simple one of the three?

Once you have at least one idea you're excited about, flesh out your plan with these prompts:

- What are you going to try to deliver at the end of the project?
  - For research projects, this might be something like 'a clear answer to the question [question]'
- If you deliver this, how well does it actually achieve the goals you set out above? If it doesn't achieve them very well, revise your goals, idea or target deliverable until they correspond.
- Are there any other ideas that might actually achieve your goals better? Set a [5 minute timer](https://www.google.com/search?q=5+minute+timer) to think this through.
- How might you achieve this deliverable in the time that you have? Are there smaller milestones you could use to check you'll be on track, or other ways to break down the task into smaller pieces?
- Imagine the project hasn't worked out. What do you think is mostly likely to have gone wrong? How could you have prevented this, or how could you at least reduce your uncertainty about this risk? Repeat this a few times, maybe considering:
  - How you'll make sure you spend sufficient time on the project
  - What other resources you might need, like compute or access to models
  - Uncertainties about how difficult technical work might be, or how software libraries work
  - Whether you'll have version control and backups of your work
- How would you want your cohort group to support you? Would you like a kind of accountability mechanism from the group?

In your final session, you'll review your plan with your cohort peers. Come prepared with a brief explanation of your project in a format that you could share: for example a Google Doc or Word Online document.
