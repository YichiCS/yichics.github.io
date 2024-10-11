---
layout: homepage
---

## About Me

Hello, I am **Yichi Zhang** (张亦弛), an undergraduate student at [Zhejiang University](https://www.zju.edu.cn/), majoring in **Information Engineering** and minoring in **Computer Science and Technology**. Currently, I am taking courses in my fourth year and participating in research work at [NESA Lab](https://nesa.zju.edu.cn/), under the guidance of Prof. [Xiaogang Xu](https://scholar.google.com/citations?user=R65xDQwAAAAJ&hl=zh-CN&oi=ao) and Prof. [Shouling Ji](https://scholar.google.com/citations?user=5HoF_9oAAAAJ&hl=zh-CN&oi=ao). I also collaborate with Prof. [Ting Wang](https://alps-lab.github.io/) as summer research intern.

<font color="#dd0000">Now I am looking for 25 Fall CS/ECE Ph.D. Opportunity.</font><br />

## Research Interest

To develop trustworthy AI systems for critical applications, I believe it is essential to address three key factors: **robustness**, **safety**, and **interpretability**. Driven by these considerations, I aim to explore the following research questions: **(i)** How can we ensure that models maintain sufficient robustness during interactions with external environments, protecting them from hidden threats? **(ii)** How can we minimize bias and harmful content in model outputs to promote fairness and reliability? **(iii)** How can we establish comprehensive benchmarks that quantifies the trustworthiness and safety of LLMs from multiple dimensions to enhancing interpretability?

<!--  -->

If you are interested in my research, please feel free to contact me by **yichics02 \[at\] gmail \[dot\] com** or **yichizhang \[at\] zju \[dot\] edu \[dot\] cn**.

## News

- **[Oct. 2024]** **Looking for 25 Fall CS/ECE Ph.D. Opportunity now.**
- **[June 2024]** One paper about Backdoor in Federated Learning will soon be released.
- **[Mar. 2024]** To become an research intern of ALPS Lab at SBU in 2024 Summer.
- **[Dec. 2023]** One paper about Generated Image Detection is released on the arXiv.

{% include_relative _includes/publications.md %}

{% include_relative _includes/services.md %}

## Research Experience

My research began through collaboration with Prof. Xiaogang Xu. At that time, I was captivated by generative models such as GANs and Diffusion Models. However, as I delved deeper into the subject, I realized the potential risks of fraud associated with AI-generated content, and the lack of reliable methods to detect such content. Traditional approaches are constrained by the training dataset, making it difficult to capture the general characteristics of generated content. In addressing this challenge, we discovered that generated images and real images display distinct differences in the estimated noise during the diffusion process, which is more pronounced than in the original image. Building on this insight, we developed a novel classification feature called Diffusion Noise Feature (DNF). Classifiers trained with DNF achieved state-of-the-art detection and generalization performance across four datasets, and demonstrated more than 20 times faster extraction speed compared to similar features. 
This work is currently under review for CVPR 2025, where I contributed as the first author, leading the development of the research idea, designing experiments, and writing the paper. Through this process, I gained essential research skills and built a solid understanding of various generative models. Additionally, I realized that AI is a double-edged sword, which sparked my deep interest in AI security.

During my research under the supervision of Prof. Shouling Ji, I focused on security and privacy issues in machine learning, particularly backdoor attacks in horizontal federated learning. We observed that most attack methods exhibit fluctuations in success rates when subjected to defenses like parameter scaling and clipping. By revisiting the assumption of weight deviation in many defense methods, we further explored the relationship between poisoned data distributions and poisoned update distributions. Based on this finding, we redesigned the backdoor triggers that closely resemble benign data distributions and crafted a novel poisoning loss that makes poisoned updates converge towards benign ones. We introduce a novel backdoor attack method called AdvFed which demonstrates strong attack performance against six different defenses across three datasets. Moreover, AdvFed boasts a longer lifespan and achieves attack efficiency by combining online and offline optimizations. 
This work has been submitted to TIFS. As the second author, I contributed significantly by refining the idea and leading the experimental works, particularly in setting up the federated learning framework and designing the poisoning loss function. After learning about the widespread security challenges in machine learning, my interest in trustworthy machine learning has deepened.

To further explore security issues in the practical applications of LLMs, I collaborated with Prof. Ting Wang at Stony Brook University as a research intern. Our research focused on leveraging low-perplexity, high-efficiency attack methods to uncover hidden security vulnerabilities in LLMs. Specifically, we constrained jailbreak suffixes within the logits space through optimization, collecting successful attack suffixes to fine-tune a Llama-2-based jailbreak suffix generator. This approach enables the generation of effective attack suffixes with just a single inference step, achieving a balance of low perplexity and minimal generation time. Our method demonstrated superior performance on datasets such as AdvBench. Additionally, we investigated poisoning attacks on graph retrieval-augmented generation (RAG) systems, which are typically resilient to standard RAG poisoning methods. By using prompt injection, we successfully altered the graph index, connecting poisoned entities with key entities, and demonstrated the effectiveness of this approach even in black-box settings.  In our future work, we will continue refining these techniques and keep contributing to the LLM security community.