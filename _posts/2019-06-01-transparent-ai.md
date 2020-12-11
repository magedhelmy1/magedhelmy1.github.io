---
title: Why Designing Transparent AI Matters?
author: Maged Helmy
date: 2019-06-01 14:00:00 +0100
categories: [Blogging, Deep Learning]
tags: [ai]
---
## Building a fair algorithm in an unfair society  

### **Abstract**
<div style="text-align: justify ">
Although Artificial Intelligence (AI) has proven to have great potential in many industrial applications [1]–[3], research lacks sufficient methods to adequately interpret and decode the internal logic of such high performing algorithms [4]. Highly performing algorithms suffer from the black-box phenomenon where the calculations cannot be validated, and the methodology behind the algorithm cannot be verified [5]. This poses several ethical challenges since such systems can reflect or amplify the existing biases of its implementers and the dataset leading to discrimination against minorities and may repel society from using such promising technologies. In this article, we argue that using AI technology without the appropriate assessment and understanding of how it arrives at its decisions outweighs the benefits and can harm the individuals and society.
</div> <br/>
### **Background**

<div style="text-align: justify ">
Deep Neural Networks (DNN), which are a subset of AI, is behind the majority of the recent successes in AI [6]. DNN can outperform a human expert in an infinitely large amount of datasets and can make more informed decisions in a shorter period [7]. For example, a DNN that is trained to diagnose cancer can be more accurate and faster than a radiologist with a Ph.D. [8]. However, these algorithms are highly complex, where the relationship between the data (input) and the conclusion (output) is uninterpretable [9]. Such algorithms pose an ethical challenge since they may inherit biases from human prejudices, which can lead to unfair decisions [5]. In light of this ethical challenge, we will present some examples of ethical dilemmas that may arise from using such high performing black box AI-based systems in decision-making processes that can have a significant impact on an individual’s human rights.
</div> <br/>
### *I. Interpretability in AI*

<div style="text-align: justify ">
<p>An interpretable AI is an algorithm that can be explainable by its implementers to society and individuals (i.e., regulatory, customers, employees). For instance, the algorithmic patterns of how the conclusion has been reached are calculable and verifiable. Many high performing DNNs are not able to present the logic of the outcome due to the depth of the networks, and trying to simplify the network to gain interpretability will significantly reduce accuracy [10]. Furthermore, an interpretable algorithm will allow audibility where an algorithm can be reviewed, tested, and refined to reflect the moral codes and principles of society. However, the literature proves that auditable algorithms have reduced performance and, in many cases, minimal functionalities [11]–[13]. Some examples of commonly used algorithms where performance and interpretability correlates are GoogLeNet [14] with 6.7 million parameters and VGGNet [15] with 138 million parameters. Therefore, an ethical dilemma is using these deep neural networks that are capable of highly sophisticated functionalities like analyzing video, audio, and texts in an uninterpretable manner, versus using an interpretable algorithm with minimal functionally and low accuracy. How much accuracy and features are we willing to sacrifice to satisfy the transparency dilemma?</p>
</div>
<div style="text-align: justify ">
<p>An example of highly opaque DNNs that has significantly increased the safety of the roads is Tesla’s autopilot system (TAS) [16]. TAS crowdsources different types of structured and unstructured data from its cars and combines them using highly deep learning algorithms [17], making it the car with the lowest probability of injury [18]. Another example of high performing but opaque systems are the AI’s algorithms deployed in smart homes. Similar to Tesla’s autopilot; it combines sensor data using deep learning algorithms to arguably increase the quality of life in homes for senior citizens and persons with disabilities [19]–[22].</p>
</div>
<div style="text-align: justify ">
<p>However, not all high performing algorithms have been transformative. An example where an interpretable algorithm could have prevented an erroneous mistake was Microsoft AI chatbot Tay which was shut down 16 hours after launch as it turned into a Hitler-loving sex robot [23]. Another dilemma in the medical world is when the tissues of a healthy-looking man are flagged as cancerous to the algorithm. Although the prediction happened to be accurate since the algorithm has learned from the data of previous patients, it could not explain how it arrived to this conclusion. This leaves the doctor and the patient with a severe dilemma since it will be hard to come up with a preventive measure without knowing what the risk factors are.</p>
</div>
<div style="text-align: justify ">
<p>Few examples where auditability matters are COMPAS [24], which is used by the U.S. courts where the algorithm is discriminant against minorities based on an ethnic prejudice in the input dataset. Another example is the algorithm used by the United States Immigration and Customs Enforcement (ICE). A risk-assessment on ICE revealed that the algorithm was manipulated to produce only one recommendation, “..detain..” all immigrants in custody [25]. Last but not least, Amazon recruiting tool [26] preferred male software developers over females due to the dataset reflecting male dominance in the tech industry.</p>
</div>
<div style="text-align: justify ">
<p>An auditable algorithm could have played an essential role in all the previous examples by allowing an unbiased third-party to verify the algorithm logic against ethical principles before deployment to prevent unjust discrimination. Society loses trust in such promising technologies when either directly or indirectly, they amplify discrimination and oppress specific individuals based on an uninterpretable logic from the dataset [27].</p>
</div>
<div style="text-align: justify ">
<p>One can argue if society is even ready to adopt such high performing algorithms when direct manipulation (in the case of ICE) or indirect human bias (in the case of Amazon) can have adverse effects on individuals? Society has witnessed the devastating effects of similar technologies[28], [29], amongst others, the atomic bomb, and the AK-47 (responsible for more deaths than any other rifle due to the cheap mass production design[30]). As of the evidence we have, one can conclude that an interpretable & auditable AI algorithm is inevitably more beneficial than a high performing algorithm that is not interpretable nor auditable.</p>
</div>
### *II. Solutions that work, kind of.*
<div style="text-align: justify ">
<p>Tech leaders like Facebook and Microsoft are investing heavily in developing tools that attempt to tackle biases in DNNs while trying to maintain all the functionalities in a high performing algorithm[31] - however useful, this does not reveal the black box but merely tries to solve the symptoms of the problem. Moreover, companies should understand that this challenge requires more than a technical fix. For example, the lack of diversity amongst the teams building the technology, and collecting the dataset makes it more challenging to overcome biases. Human biases and prejudice implicitly gets reflected in the data collected [32]. Therefore, tech companies should also invest in educating the developers, programmers, and the data collectors to understand the moral principles and consequences that may result from developing such technologies solely based on results and profit. Moreover, companies should invest more in transparent AI to make it possible to scrutinize the logic and accustomed it to social and judicial expectations.</p>
</div>
<div style="text-align: justify ">
<p>Furthermore, there are several methods in the literature on controlling the quality of the input to address algorithmic biases, which inevitably controls the output of the algorithm [33]. However, right, it will not be straightforward to detect if the dataset has been tampered with or hacked since the logic of the algorithm is still a black box. There are some other methods proposed that can reconstruct the algorithm to an extent by reverse-engineering the output into the input [34]. However, this does not adequately address the issue of the black box but rather try to deduce the algorithm based on experimental science.</p>
</div>
<div style="text-align: justify ">
<p>To conclude, by favoring a transparent AI approach over a highly functional one, it will encourage AI implements to first understand the technology more thoroughly before implementing it. This may in turn reduce unpropitious consequences. </p>
</div>
### *III. Wait...What about Companies Competitive Advantage?*
<div style="text-align: justify ">
<p>Companies trade secrets can be lost if the algorithms are open for the public to test and scrutinize. Companies can also lose their competitive advantage if the logic gets replicated by other companies in countries where trade secrets and protection are not enforced or even applicable. However, when it comes to AI, nearly all tech leaders like Google [35] and Facebook [36] have open-sourced their AI technology. While debatable on why the tech leaders decided to do that, up to this day, regulations of applying AI have no satisfactory legal terms where companies can disclose their algorithms without harming their competitive advantages since the law stresses the auditability of the algorithm [37]. Therefore, as more companies thrive to open-source their AI technology to the public, this will inevitably increase the public trust in such emerging technology.</p>
</div>
<div style="text-align: justify ">
<p>Moreover, after the introduction of the GDPR in May 2018, the EU has created a panel to present a study on the governance of algorithmic accountability and transparency [37]. The study, which was published in April 2019, has concluded that there is no convincing evidence that black box algorithms provide the necessary safeguards required to the people and society when using such technology. The panel also recommended establishing a permanent global ‘Algorithm Governance Forum’ and giving regulatory agencies the rights to hold parties accountable for violations of European laws and human rights by using such black box algorithms. Another report was also released in 2019 by the EU, titled “Ethics guidelines for trustworthy AI” which stressed the reproducibility and traceability of AI algorithms [38]. Therefore, one can argue that a transparent AI might be the only competitive advantage in the future when the industrial frameworks are established and come into force.</p>
</div>
<div style="text-align: justify ">
<p>Many companies face a competitive time pressure to get their software to market since their software must strictly adhere to its industry conformance certificates [39]. To mitigate such limitations, heavily regulated industries like aviation, finance, and medical devices have developed a set of certification models that can fast track software conformances for devices with lower risks [40]. Currently, there are no similar fast track routes to certify AI algorithms in the mentioned industries; therefore, time to market (TTM) is not a competitive factor for AI algorithms.</p>
</div>
<div style="text-align: justify ">
<p>One can argue that the competitive advantage will belong to the companies that prioritize and prove an interpretable and auditable algorithm rather than the companies with the highest performing opaque algorithms. When the tech race is switched from the highest performing algorithm to the most interpretable and auditable algorithm, such technologies may start to gain the public trust.</p>
</div>
### *Conclusion*
<div style="text-align: justify ">
<p>AI, and specifically deep learning, has proven to outperform human experts in their domain fields. However, such high performing algorithms come at the cost of interpretability where higher-performing algorithms are less interpretable then their lower-performing counterparts. This is due to the nature of how deep neural networks are built. The ethical dilemma is whether to use these high performing algorithms at the expense of interpretability, auditability, and transparency. </p>
</div>
<div style="text-align: justify ">
<p>In this article, we have presented some examples where a high performing algorithm may reinforce human biases and prejudices, and therefore a more interpretable is admissible even if it comes at the cost of losing functionalities. Creating and using interpretable algorithms can build public trust towards such emerging technologies. </p>
</div>
<div style="text-align: justify ">
<p>It is essential to highlight that the current solutions provided by the tech industries to deal with the black box phenomena addresses the symptoms but not the issue directly. Moreover, due to the tradition of how the industry is built, companies argue that the trade secrets will be lost if algorithms are made available for the public to scrutinize. However, it is essential to note that current regulations do not allow the deploying or usage of such high performing algorithms as it has proven to be discriminant and sexist. Therefore, at the current stage, an acceptable AI will be a transparent, interpretable, and auditable AI.</p>
</div>
<div style="text-align: justify ">
<p>Since the current high performing algorithm is not capable of satisfying the social and judicial expectations, a ‘watered-down’ transparent version of AI can be implemented. Algorithms transparency and accountability must be high on the agenda of AI implementers as it is the only way to gain a competitive advantage when the regulations come into force. AI implementers should understand that technologies should be made to combat discrimination and injustice and not merely reinforce human prejudices and social unfairness.</p>
</div>

### Get in Touch

Feel free to get in touch anywhere, anytime ! <br/>
[LinkedIn](https://www.linkedin.com/in/helmy47/) or Email me directly maged.helmy1@outlook.com <br/>


To contribute, simple create a pull request on the Github page! :)


[References are here](https://github.com/magedhelmy1/Transparent-AI/blob/master/Reference%20List)
