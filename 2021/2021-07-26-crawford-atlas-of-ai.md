July 26, 2021

I picked this book up in a bookshop called [Left Bank Books Collective](https://www.leftbankbooks.com/) at Pike Place in Seattle.

#### Introduction
##### Summary
Crawford frames the holistic discussion of AI using two analogies anchored by anecdote.

The first is about "Clever Hans", a horse who became famous at the turn of the 20th century for apparently being able read and solve math problems, among other things. In reality, Hans wasn't exhibiting intelligence as his audience was expecting; instead, he was picking up on subtle cues from his trainer, who would inadvertently indicate with facial features when Hans had arrived at the right answer. Crawford implies that AI - like Hans - may not be exhibiting intellegence in the way we expect.

The second is about maps and atlases. Crawford discusses maps and atlases made in the middle ages; while they attempted to provide an objective view of the surrounding landscape, they also encoded baises implicit among those who created them. Likewise, AI is knowledge about the world that's been flash-frozen. Moreover, it contains biases of its creators, not only in the training data used (which is the knowledge that is crystallized), but also in the objectives for which the AI systems were created.

Crawford finishes with a summary of the chapters in the book.

##### Discussion
I think that Crawford's analogies are interesting and apt. The Clever Hans felt like a little bit of a stretch and wasn't so interesting, but the one about maps and atlases was spot on.


#### Chapter 1: Earth
##### Summary
Crawford discusses the impact of AI, technologies related to AI, and past technologies on the planet.

Chapter 1 opens with a discussion of Lithium mining's impact on the planet, making analogies to California's earlier gold and silver rushes. This section is poingnant, calling up historical images of towns that existed for only a few years before they had stripped the earth of its resources and drawing parallels with modern lithium mining operations. She also discusses the relative time scale of the non-renewable resources that we're mining with the decade-long lifetime of the devices they comprise:

> we are extracting Earth's [4.5 billion year] geological history to serve a split second of contemporary technological time, building... [iPhones] designed to last for only a few years.

Crawford also discusses the use of "conflict" minerals in computing devices. Some companies have shown interest in tracing the provenance of their raw materials - ostensibly to ensure that they're ethical - but Crawford discusses the immense complexity of this iundertaking.

Crawford gives another historical anecdote that mirrors modern mining for Lithium and "conflict minerals" - the harvesting of the Palaquium Gutta tree. To feed the appetite of 19th century Europe for latex, the tree was harvested to near extinction in less than 50 years using the power of exploited human labor.

Finally, Crawford goes for AI's environmental juglar - its power consumption (famous 2019 Strubell et. Al paper saying that training a Transformer NLP model with network arch search takes ~5x the lifetime CO2 emission of a car) and water consumption (for cooling). Not only does training AI models require staggering amounts of energy, AI also depends on some hidden costs, like the power needed to transport raw materials used to materially build hardware powering AI.

Crawford concludes the chapter by making the case that AI is an enormous machine, and its tendrils are irrevocably intertwined - from research on NN architectures to mining for minerals used to make capacitors, you can't ignore any details without unwinding the whole tapestry.

##### Discussion
The tenor of this book overall - as far as I can tell - is that AI can't be considered in a vacuum. The logistics of the technology it rests on need to be considered as well. In this chapter, Crawford points to specific ecological impacts that AI has. Some are more valid than others: even if it's hard to deny, the connection Crawford draws between AI and Lithium is tenuous (although it does give rise to some of the most poingnant writing in this chapter).

More compelling is the discussion on "conflict minerals" (a term which Crawford (perhaps rightfully) asserts is euphemestic), which are needed for the very hardware that ANY AI must run on (save the 20kHz all-plastic cortex M0+ published in 2021) and the discussion on power consumption. Crawford's criticisms are rightfully scathing, however, I think it's also within her purview to discuss mitigations to these issues: emerging mat-sci research is beginning to offer more sustainable alternatives for IC fabrication, and alternative energy generation technologies are not only improving faster than ever - being all-electric, AI is already primed to be switched over to these new methods once more infrastructure is in place.


#### Chapter 2: Labor
##### Summary
Crawford discusses AI's strained relationship with labor by weaving together views from 2 angles: how AI influences the way work is done, and how AI itself is powered by exploitative labor practices.

In the modern day, AI is being used to further commodify workers. Amazon warehouse fullfillment centers are undergirded by the assumption that workers will deliver their tasks with second-level precision. The underlying principle is workers keeping "the rate", a point of contention between Amazon and labor unions. The former uses "the rate" as a fundamental law to ensure astonishingly fast delivery times while the latter claims that it's subjecting workers to inhumane working conditions. "The rate" that workers are expected to deliver is allocated by AI-based algorithms; AI is influencing the way work is done.

The situation at Amazon is merely the newest chapter in a long history of worker exploitation that's been going on since the dawn of the industrial revolution. Earlier technological advances were harnessed (or were in service of) divorcing workers from the products of their labor so that industrial scalability could be achieved. Crawford gives several anecdotal examples of this happening, including the the panopticon (a structure enabling better worker supervision), Ray Croc's carefully-timed burger making procedures (enabling faster and cheaper hamburgers), and methods for animal butchery employed at factory-scale operations in Chicago in the 1870s. There's overlap between these, but the rub is that workers are made replacable and dispensible and we get closer to an 'ideal' where the time of completely unskilled laborers is a raw material used to make goods - there's no individuality or personal enrichment to consider (indeed, this vision was almost explictly articulated by Charles Babbage (yes, that Babbage): Crawford describes the factory as a giant computing machine and humans within as interchangable, standardized components which may or may not be faulty).

And so AI is another tool in toolbelt of management to more thoroughly take advantage of workers by scheduling them more exploitatively and by making their work as brutal as possible without going beyond the pale.

This is how AI influences work, but there's a way in which work influences AI. A major emerging sector of work is in the labelling of data to feed to AI models. Crawford argues that - once one considers the amount of labelled data going into training - it's hardly surprising that we can make systems which recognize faces or classify text. Oftentimes the perfomance of a system isn't contingent on the ingenuity of the system itself, but on the quality of the labelled data, perhaps leading to a 'Clever Hans' scenario. Moreover, this work is often highly exploitative, with people earning less than minimum wage in an unregulated freelance economy to do work that's sometimes traumatizing (in the case of flagging abusive content). In some extreme cases, companies have tried to pass off the outsourcing of tasks to human workers as genuine AI, a true "Mechanical Turk" scenario.

##### Discussion
I find Crawford's criticism to be largely valid, however, she coalesces 2 issues (AI as a tool to exploit workers, and exploitation of workers as a fuel to power AI) into a single chapter. These would stand better and with more clarity on their own.

Unlike some of the stuff in the first chapter, these things are harder to sidestep. We can come up with beyond-CMOS techniques and alternative energy sources that alleviate environmental concerns, but vast quantites of labelled data are baked into AI techniques; besides that, AI will always be begging to be used as cudgel against workers as long as we have a framework for exploitation of laborers.

One thing that Crawford does from time to time that bugs me is apparent misunderstanding of technical topics for the sake of poetry. In this chapter, Crawford criticizes a time synchronization protocol that Google has standardized by saying that its technique of "slow[ing] down to wait out that uncertainty" is "[an embodiment of] the fantasy of slowing down time" (p.79), which seems to me to be a deliberate misunderstanding of a technical topic for a cheap and silly pot-shot at Google. She also criticizes the use of the terms "master" and "slave" in technology; to be sure, these terms DESERVE CRITICISM and MUST BE DEPRECATED, but her criticism is misplaced, incomplete, and detracts from the power of this chapter.

#### Chapter 3: Data
##### Summary
A fundamental tenet of our current AI techniques is a massive thirst for data. Researchers and commercial entities are willing and able to feed their AI systems vast quantites of low-quality data. Oftentimes, this data is biased (as in the case of facial datasets), inaccurate (as in the case of the CalGang database), invasive of privacy (as in the case of the mug shots), collected without consent, or stripped of context. When AI data has these characteristics, it invariably leads to harm.

The techniques that we know as AI/ML today didn't start until the mid-1980s, when researchers turned to statistical approaches after the failures that led to the "AI winter" (p. 99). These statistics and data based approaches are still in use today. From the start, they required massive amounts of data. Crawford illustrates by describing the work of an IBM speech recognition group. Their work relied on prodigious amounts of text data taken from wherever they could find it (technical manuals, kids books, patents, and even an anti-trust lawsuit against IBM were all consumed).

This thirst for data can be handled in more or less responsible ways. Crawford identifies the FERET database - a training dataset of faces collected by the DoD for training facial recognition - as a "high-water mark" in responsibly-collected and curated AI datasets. It's worth remarking that this "high water-mark" was collected for malicious reasons and is not very diverse. Imagenet, which could be seen as the successor of FERET, is a lot worse. Organized by AI superstar Fei-Fei Li, Imagenet was created by scraping millions of images from the internet, stripping them of their context, and asking underpaid MTurk workers to classify the images according to classes in WordNet (a database of semantic relationships between words). Basically all images were used without consent, and because of limited oversight, many were classified with labels that reinforce harmful stereotypes.

In the worst cases, dataset choice can bring direct harm to individuals (datasets released by the NYC Taxi and Limo Commission allowed for doxxing of cab drivers and occupants via statistical analysis even after personal data was scrubbed) and groups of people (a project predicting gang association was fed data from the LAPD's biased and inaccurate gang database). Moreover, data can be collected of people without their consent and without context, something that can easily be considered abusive or exploitative.

##### Discussion
The most obvious way that AI datasets can be harmful is through bias, but Crawford explores other ways that AI datasets can be harmful. There's a discussion here that - like in the other chapters - Crawford doesn't really have: are there ways that these concerns can be assauged?

#### Chapter 4: Classification
##### Summary
One of the most common tasks for AI systems is classification. The categories used to classify things is often


##### Discussion
I see the harm of categorization as lying on a spectrum. Classifying some things - like the type of particle observed in an accelerator - causes little or no harm; as long as you're willing accept the laws of physics as fact and not cultural artifact (which not all schools of thought are willing to do), there's no cultural context to classifiying a sensor reading as coming from a specific particle, and no harm is done by doing so. Classifying other things - like handwritten numbers - are at a low (but still nonzero) risk for harm; handwriting is a cultural artifact, so classifying it leaves the door open to undue bias, moreover, misclassifying handwritten digits could lead to material harm in some cases, but this isn't the most likely scenario IMO. Other things - like resumes - have a very high risk of harm; what constitues a "good" resume is incredibly ripe for undue prejudice due to the cultural context required to interpret it.

My half-baked perception of this is that the more heavily a category relies on social, political, or cultural construction, the more likely a classifier is to cause harm by classifying things into those categories.
