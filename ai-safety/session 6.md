# AI Safety Fundamentals: Session 6 - Technical Governance Approaches

[toc]

------



# Goals

**How might we measure and mitigate the risks of deploying AI models?**

If we are able to create extremely powerful AI systems without solving the alignment problem, rigorous technical governance approaches will be critical for mitigating the risks posed by these AI systems. Pre-deployment testing, AI control techniques, and global coordination approaches (such as pausing) could all play a role in limiting dangerous AI capabilities.

Even if we do solve the alignment problem, technical governance methods will still likely be important for some time to limit misuse or the fallout from AI malfunctions. In addition, many of this research is valuable for mitigating existing AI harms.

##### By the end of the session, you should be able to:

- Explain the need for technical AI governance work
- Critically evaluate approaches to:
  - Pre-deployment testing of powerful AI systems, including red-teaming and evaluations
  - Post-deployment management of powerful AI systems, including content filtration and API monitoring
  - Other governance methods for powerful AI systems, including watermarking of AI-generated content and compute governance

# Readings

## [**Emerging processes for frontier AI safety**](https://www.gov.uk/government/publications/emerging-processes-for-frontier-ai-safety/emerging-processes-for-frontier-ai-safety) by UK Government (2023)

> This document gives a good summary of nine common approaches to AI governance that can be implemented by AI companies acting alone (also accessible as a [PDF](https://assets.publishing.service.gov.uk/media/653aabbd80884d000df71bdc/emerging-processes-frontier-ai-safety.pdf)).

**1. Responsible capability scaling** provides a framework for managing risk as organisations scale capability of frontier AI systems. It enables companies to prepare for potential future, more dangerous AI risks before they occur, as well as manage the risks associated with current systems. Practices involve conducting thorough risk assessments, pre-specifying risk thresholds and committing to specific mitigations at each of those thresholds and being prepared to pause development or deployment if those mitigations are not in place.

7 suggested categories of practice regarding responsible capability scaling:

1. Conducting thorough risk assessments before developing or deploying new models, complemented with continual monitoring (incorporating, for example, evaluation results, evidence from earlier models, and expert forecasts)
2. Pre-specifying ‘risk thresholds’ that limit the level of acceptable risk (a level of risk of, for instance, cyberattacks or fraud that it would be unacceptable for a model release to create)
3. Pre-committing to specific additional mitigations for systems at each risk threshold, followed by a residual risk assessment
4. Adapting mitigations to the relevant stages of deployment, recognising that models may be used in different ways and contexts than intended
5. Making preparations to pause development and/or deployment if risk thresholds are reached without the pre-agreed mitigations
6. Share details of risk assessment process and risk mitigation measures with relevant government authorities and other AI companies
7. Committing to robust internal accountability and governance mechanisms, alongside external verification (for example, internal risk governance, record-keeping, independent audits)

As capability scales, many questions surrounding model development and deployment will warrant significant care. These questions include:

- what models to develop and how
- what level of security these models warrant during development
- whether and how to deploy a model, for instance whether it should be deployed through an API or open-sourced
- what datasets to use in training
- what guidance, if any, to provide to users
- what safeguards to be put in place

**2. Model Evaluations and Red Teaming** can help assess the risks AI models pose and inform better decisions about training, securing, and deploying them. As new capabilities and risks can appear as frontier AI models are developed and deployed, evaluating models for several sources of risk and potential harmful impacts throughout the AI lifecycle is vital. External evaluation by independent, third party evaluators can also help to verify claims around the safety of frontier AI systems.

**3. Model Reporting and Information Sharing** increases government visibility into frontier AI development and deployment. Information sharing also enables users to make well-informed choices about whether and how to use AI systems. Practices involve sharing different information about their internal processes, safety and security incidents, and specific AI systems with different parties, including governments, other frontier AI organisations, independent third parties, and the public, as appropriate.

**4. Security Controls Including Securing Model Weights** are key underpinnings for the safety of an AI system. If they are not developed and deployed securely, AI models risk being stolen or leaking secret or sensitive data, potentially before important safeguards have been applied. It is important to consider the cyber security of AI systems, as well as models in isolation, and to implement cyber security processes across their AI systems, including their underlying infrastructure and supply chains.

**5. Reporting Structure for Vulnerabilities** enables outsiders to identify safety and security issues in an AI system. This is analogous to how organisations often set up ‘bug bounty programs’ for vulnerabilities in software and IT infrastructure. Practices include setting up a vulnerability management process that would cover many vulnerabilities - such as jailbreaking and prompt injection attacks - and have clear, user-friendly processes for receiving vulnerability reports.

**6. Identifiers of AI-generated Material** provide additional information about whether content has been AI generated or modified. This can help prevent the creation and distribution of deceptive AI-generated content. Investing in developing techniques to identify AI-generated content is important in a highly nascent field, as well as exploring the use of approaches such as watermarks and AI output databases.

**7. Prioritising Research on Risks Posed by AI** will help identify and address the emerging risks posed by frontier AI. Frontier AI organisations have a particular responsibility and capability to conduct AI safety research, to share their findings widely, and to invest in developing tools to address these risks. Collaboration with external researchers, independent research organisations, and third-party data owners will also be key to assessing the potential downstream social impacts of their systems.

**8. Preventing and Monitoring Model Misuse** is important as, once deployed, AI systems can be intentionally misused for harmful outcomes. Practices include establishing processes to identify and monitor model misuse, as well as implementing a range of preventative measures, and continually reviewing their effectiveness and desirability over time. Given the serious risks that misuse of frontier AI may pose, preparations could also be made to respond to potential worst-case misuse scenarios.

**9. Data Input Controls and Audits** can help identify and remove training data likely to increase the dangerous capabilities their frontier AI systems possess, and the risks they pose. Implementation of responsible data collection and cleaning practices can help to improve the quality of training data before it is collected. Careful audits of training data- both by frontier AI organisations themselves and external actors can also enable the identification of potentially harmful or undesirable data in training datasets. This can inform subsequent mitigatory actions, such as the removal of this data.

## [**Computing Power and the Governance of AI**](https://www.governance.ai/post/computing-power-and-the-governance-of-ai) by Lennart Heim, Markus Anderljung, Emma Bluemke et al. (2024)

> This is a brief introduction to compute governance, which aims to use computing power as a policy lever to promote AI safety.

*From the post:*

> Computing power – *compute* for short – is a key driver of AI progress. Over the past thirteen years, the amount of compute used to train leading AI systems has increased by a factor of 350 million. This has enabled the major AI advances that have recently gained global attention.
>
> *‍*Governments have taken notice. They are increasingly engaged in *compute governance*: using compute as a lever to pursue AI policy goals, such as limiting misuse risks, supporting domestic industries, or engaging in geopolitical competition. 
>
> There are at least three ways compute can be used to govern AI. Governments can: 
>
> - Track or monitor compute to gain **visibility** into AI development and use
> - Subsidise or limit access to compute to shape the **allocation** of resources across AI projects
> - Monitor activity, limit access, or build “guardrails” into hardware to **enforce** rules
>
> Compute governance is a particularly important approach to AI governance because it is feasible. Compute is *<u>detectable</u>*: training advanced AI systems requires tens of thousands of highly advanced AI chips, which cannot be acquired or used inconspicuously. It is *<u>excludable</u>*: AI chips, being physical goods, can be given to or taken away from specific actors and in cases of specific uses. And it is *<u>quantifiable</u>*: chips, their features, and their usage can be measured. Compute’s detectability and excludability are further enhanced by the <u>*highly concentrated* structure of the AI supply chain</u>: very few companies are capable of producing the tools needed to design advanced chips, the machines needed to make them, or the data centers that house them. 

![image-20240415151428853](../../assets/typora_images/image-20240415151428853.png)

![image-20240415151818966](../../assets/typora_images/image-20240415151818966.png)

> ## Compute governance can be ineffective
>
> Although compute governance *can* be an effective regulatory tool, it may not always be the right one to use. It is one option among many for policymakers. 
>
> For example, compute governance may become less effective as algorithms and hardware improve. Scientific progress continually [decreases the amount of computing power needed](https://epochai.org/blog/revisiting-algorithmic-progress) to reach any level of AI capability, as well as [the cost to perform any number of computations](https://epochai.org/blog/trends-in-machine-learning-hardware). As the power and cost necessary to achieve any given AI capability decreases, these metrics will become less detectable and excludable. 
>
> On a related note, compute may be an inappropriate tool to govern low-compute specialised models with dangerous capabilities. For example, AlphaFold 2 achieved superhuman performance on protein folding prediction using fewer than 1023 operations – two orders of magnitude [less compute than models like GPT-4](https://epochai.org/data/epochdb/visualization). Compute governance measures to limit the development models risk also limiting the development of similarly-sized, but harmless, models. In other words, compute governance measures seem most appropriate for risks originating from a small number of compute-intensive models.
>
> ## Compute governance can be harmful
>
> Perhaps more importantly, compute governance can also cause harm. Intrusive compute governance measures risk infringing on civil liberties, propping up the powerful, and entrenching authoritarian regimes. Indeed, some things are better ungoverned. 
>
> *‍*Certain compute governance efforts, especially those aimed at increasing visibility into AI, may increase the chance that private or sensitive personal or commercial information is leaked. AI companies, users of AI systems, and compute providers all go to great lengths to preserve the integrity of their and their customers’ data. Giving more actors access to such information raises the chance of data leakage and privacy infringement. 
>
> *‍*Large concentrations of compute are also an increasingly crucial economic and political resources. Centralising the control of this resource could pose significant risks of abuse of power by regulators, governments, and companies. Companies might engage in attempts at regulatory capture, and government officials could see increased opportunities for corrupt or power-seeking behaviour. 

## [**AI Control: Improving Safety Despite Intentional Subversion**](https://www.alignmentforum.org/posts/d9FJHawgkiMSPjagR/ai-control-improving-safety-despite-intentional-subversion) by Buck Shlegeris, Fabien Roger, Ryan Greenblatt et al. (2023)

> AI control aims to explore setups that reduce risks from advanced AI systems, even where your AI systems might be misaligned.
>
> This forum post summarises an empirical approach where they tested different AI control methods to see how well they performed: both in terms of usefulness (how much of the performance of the model are you recovering) and safety (how often can the model do something misaligned).

*From the paper:*

> As large language models (LLMs) become more powerful and are deployed more autonomously, it will be increasingly important to prevent them from causing harmful outcomes. Researchers have investigated a variety of safety techniques for this purpose, e.g. using models to review the outputs of other models, or red-teaming techniques to surface subtle failure modes. However, researchers have not evaluated whether such techniques still ensure safety if the model is itself intentionally trying to subvert them. In this paper, we develop and evaluate pipelines of safety techniques (“protocols”) that are robust to intentional subversion.

## [**AI Watermarking Won't Curb Disinformation**](https://www.eff.org/deeplinks/2024/01/ai-watermarking-wont-curb-disinformation) by Jacob Hoffman-Andrews (2024)

> This short blog post explains how different types of identifiers to flag AI generated content might work, and what they might or might not be useful for.

<u>Summary:</u> AI watermarking is tricky to implement and likely won't work in preventing disinformation. Watermarking genuine content is a more viable alternative likely to succeed but comes with it's own issues and potential vulnerabilities.

## [**Challenges in evaluating AI systems**](https://www.anthropic.com/news/evaluating-ai-systems) by Anthropic (2023)

> There are many difficulties implementing even 'simple' evaluations for AI systems. This article explores some of the open technical and non-technical problems with evaluations and red-teaming.
>
> While reading, consider reflecting on how many of these problems seem analogous to problems with RLHF.

*From the post:*

> In this post, we discuss some of the challenges that we have encountered in developing AI evaluations. In order of less-challenging to more-challenging, we discuss:
>
> 1. Multiple choice evaluations
> 2. Third-party evaluation frameworks like BIG-bench and HELM
> 3. Using crowdworkers to measure how helpful or harmful our models are
> 4. Using domain experts to red team for national security-relevant threats
> 5. Using generative AI to develop evaluations for generative AI
> 6. Working with a non-profit organization to audit our models for dangerous capabilities
>
> We conclude with a few policy recommendations that can help address these challenges.

## [**AI Governance Needs Technical Work**](https://www.aisafetyfundamentals.com/blog/ai-governance-needs-technical-work) by AI Safety Fundamentals (2022)

> This article explains opportunities for technical work within AI governance, as well as lists practical next steps to explore careers in technical AI governance work.

*From the post:*

> 

# Exercises

##### Investigate an intervention

Pick one of the following technical AI governance interventions:

- [Compute governance](https://www.governance.ai/post/computing-power-and-the-governance-of-ai): controlling access to and use of computing resources like AI chips.
- [On-chip mechanisms](https://s3.us-east-1.amazonaws.com/files.cnas.org/documents/CNAS-Report-Tech-Secure-Chips-Jan-24-finalb.pdf): hardware advancements that enable other measures, like compute governance or content provenance.
- [Data input controls](https://www.gov.uk/government/publications/emerging-processes-for-frontier-ai-safety/emerging-processes-for-frontier-ai-safety#data-input-controls-and-audits): filtering data used to train AI models, e.g. removing hateful content or personal information.
- [Evaluations](https://arxiv.org/pdf/2305.15324.pdf): testing AI systems against standardised benchmarks to assess behaviours.
- [Red-teaming](https://cset.georgetown.edu/article/what-does-ai-red-teaming-actually-mean/): more exploratory testing to find vulnerabilities or exploit AI systems (also see [adversarial machine learning](https://en.wikipedia.org/wiki/Adversarial_machine_learning))
- [Enabling third-party auditing](https://static1.squarespace.com/static/6593e7097565990e65c886fd/t/65a6f1389754fc06cb9a7a14/1705439547455/auditing_framework_web.pdf): enabling third parties to effectively inspect AI systems safely and securely.
- [Input/output filtration](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/content-filter): reviewing prompts and responses, and blocking requests that are flagged by some policy.
- ['Know-your-customer' controls](https://cdn.governance.ai/Oversight_for_Frontier_AI_through_a_KYC_Scheme_for_Compute_Providers.pdf): identifying and vetting users of AI systems, e.g. only known biologists should have access to models that explain high-risk synthetic biology concepts.
- [Abuse monitoring](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/abuse-monitoring): monitoring for harmful applications of AI systems, e.g. looking at patterns of behaviour (potential parallels with [anti-money laundering](https://en.wikipedia.org/wiki/Anti–money_laundering)).
- [Watermarking](https://huggingface.co/blog/watermarking): marking outputs from AI systems to enable identification of AI generated content.
- [Hash databases and perceptual hashing](https://www.ofcom.org.uk/__data/assets/pdf_file/0036/247977/Perceptual-hashing-technology.pdf#page=3): maintaining records of AI-generated or human-generated content, or subsets of it.
- [Content provenance](https://c2pa.org/): marking outputs from non-AI generated systems, such as cameras to prove authenticity.
- [Information security standards](https://www.ncsc.gov.uk/collection/guidelines-secure-ai-system-development) ([alt](https://www.anthropic.com/news/frontier-model-security)): establishing and enforcing cybersecurity measures at AI labs, or for AI systems.
- [Audit logging](https://arxiv.org/pdf/2004.07213.pdf#page=26) (section 3.1): proportionate, secure and privacy-preserving logging of AI system operations for after-the-fact auditing.
- [Agent identification](https://arxiv.org/pdf/2401.13138.pdf#page=7) (section 3.1 - also [section 4.6 here](https://cdn.openai.com/papers/practices-for-governing-agentic-ai-systems.pdf#page=13)): in a world with many AI agents, being able to understand which agents are taking actions on behalf of which actors.
- OSINT monitoring: using open source intelligence for monitoring compliance with AI treaties, e.g. detecting AI chip supply chain leaks.

**Answer the following with regards to your selected intervention:**

> <u>I selected **compute governance**</u>

1. *What is this intervention in your own words?*
   1. Restricting and monitoring access to compute resources to actively direct and as necessary, curb, AI development
2. *How much could it reduce risks from intent aligned AI systems?*
   1. Significantly - by slowing down development or restricting the actors that are permitted to develop AI and providing a lever of controlling their development of it
3. *How much could it reduce risks from the misalignment of advanced AI systems?*
   1. Significantly - as the electricity could basically be pulled from certain projects, organisations and applications
4. *What other interventions could complement this one?*
   1. Directing focus areas of AI research and application development, perhaps treating it as a consumer product, like food, with certain stringent regulations to guide it's offerings and consumption
5. *What work has already been done on this and how well does it work so far? (you may need to review the further resources, or do some internet research)*
   1. Uncertain, it seems some field surveying has been done in characterising the landscape of the chip manufacturing supply chain and the technicalities of the hardware and how it might be constrained in it's capabilities to prohibit certain types of uncontrolled usage etc. Some work also seems to have been done on how to monitor usage - monitoring network traffic on compute platforms, satellite imagery to identify data centers etc.
6. *How could you effectively implement this or a part of it?*
   1. 

# Thoughts

