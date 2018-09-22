# Annotated bibliography for commonsense learning and reasoning
Michihiro Yasunaga


## Commonsense knowledge base (general)
-	ConceptNet [[paper](http://alumni.media.mit.edu/~hugo/publications/papers/BTTJ-ConceptNet.pdf)] [[website](http://conceptnet.io/)]
-	DBpedia [[website](https://wiki.dbpedia.org/)]
-	YAGO [[website](https://www.mpi-inf.mpg.de/departments/databases-and-information-systems/research/yago-naga/yago/)]
-	Google knowledge graph [[website](https://developers.google.com/knowledge-graph/)]
-	[Commonsense Knowledge Base Completion](http://aclweb.org/anthology/P16-1137) (ACL'16)
-	[WebChild 2.0: Fine-Grained Commonsense Knowledge Distillation](http://www.aclweb.org/anthology/P17-4020) (ACL'17)
-	[Automatic Extraction of Commonsense LocatedNear Knowledge](http://www.aclweb.org/anthology/P18-2016) (ACL'18)



## Physical/Grounded commonsense
Physical commonsense, such as knowledge about actions, physical properties and relationships between objects, is a key to both language understanding and visual reasoning.   
__

[**Verb Physics: Relative Physical Knowledge of Actions and Objects**](https://arxiv.org/pdf/1706.03799.pdf) [[project page](https://uwnlp.github.io/verbphysics/)]

Maxwell Forbes, Yejin Choi (ACL'17)


Aims to learn various physical properties (weight, size, speed, etc.) automatically from unstructured textual data. The key idea is to look at action verbs to infer the physical relationships between objects. For example, we do not say "I am larger than a ball" or "a ball can move faster than I", but we can infer these facts from a sentence like "I threw a ball", which we do say in daily life. This allows us to overcome the reporting bias and extract the unspoken knowledge from language.

***

[**Extracting Commonsense Properties from Embeddings with Limited Human Guidance**](http://aclweb.org/anthology/P18-2102)

Yiben Yang, Larry Birnbaum, Ji-Ping Wang, Doug Downey (ACL'18)

Employes a zero-shot learning model to learn the commonsense properties (same task as above), with substantially less manual annotation. The model takes the form of a neural network that compares a projection of embeddings for each of two objects (e.g. "elephant" and "tiger") to the embeddings for the two poles of the target dimension of comparison (e.g., "big" and "small" for the size property). The projected object embeddings are trained to be closer to the appropriate pole.

***

[**What Action Causes This? Towards Naive Physical Action-Effect Prediction**](http://aclweb.org/anthology/P18-1086)

Qiaozi Gao, Shaohua Yang, Joyce Y. Chai, Lucy Vanderwende (ACL'18)

Introduces a new task: action-effect prediction. Given an action description (e.g., "slice an apple"), we want to predict the result state in both language ("apple is split into pieces") and visual descriptions. Such action-effect knowledge/prediction plays a key role in reasoning about actions (so applicable to robotics), but was not covered by previous commonsense knowledge bases. The paper creates a new dataset and develops machine learning models to automatically perform this prediction task.

***

[**Swag: A Large-Scale Adversarial Dataset for Grounded Commonsense Inference**](https://arxiv.org/pdf/1808.05326.pdf) [[Project page](https://rowanzellers.com/swag)]

Rowan Zellers, Yonatan Bisk, Roy Schwartz, Yejin Choi (EMNLP'18)

Presents a new dataset that tests grounded commonsense. Here, grounded commonsense means that given a description (e.g. “she opened the hood of the car”), humans could imagine the situation and anticipate what is likely to come next (e.g. "then, she examined the engine"). The task consists of a starting senence and multiple choices for the next sentence, similar to the format of the natural language inference (NLI) dataset and Story Cloze Tests. To prevent human biases in creating multiple choices (often stylistic biases; see below), the authors propose Adversarial Filtering, which iteratively trains an ensemble of stylistic classifiers and filters out biased endings.



## Social commonsense

[**Event2Mind: Commonsense Inference on Events, Intents, and Reactions**](https://arxiv.org/pdf/1805.06939.pdf) [[Project page](https://uwnlp.github.io/event2mind/)]

Hannah Rashkin, Maarten Sap, Emily Allaway, Noah A. Smith, Yejin Choi (ACL'18)

Understanding a narrative often needs commonsense inference about the mental states of people in relation to events. For example, if "Person X is dragging his feet at work", we can trivially infer that X's intent is "X wants to avoid doing things", X's emotional reaction can be feeling "lazy", and while not mentioned explicitly, people around him might be affected by the situation and feel "frustrated". The paper studies the feasibility to develop a NLP model to infer humans' intent and reaction given an event description. To this end, the paper creates a large dataset for this task by collecting event descriptions (e.g., "PersonX gives PersonY a gift"), and for each event the possible intents of X and reactions of X and Y. Using this dataset, they train a neural network model that given an event description, encodes it and jointly decodes X's intent, X' reaction, and Y' reaction descriptions.

***

[**Modeling Naive Psychology of Characters in Simple Commonsense Stories**](https://arxiv.org/pdf/1805.06533.pdf) [[project page](https://uwnlp.github.io/storycommonsense/)]

Hannah Rashkin, Antoine Bosselut, Maarten Sap, Kevin Knight, Yejin Choi (ACL'18)

Similarly, this paper's motivation is to address the inference of character’s mental states behind events in commonsense stories. This paper develops a new dataset and annotation formalism that densely label short stories. The annotation provides a chain of motivations and emotional reactions for each character as the story proceeds. The annotation also includes mental state changes for entities even when they are not mentioned directly in a sentence.


## Reading comprehension
### ROCStories Cloze Task [[web page](http://cs.rochester.edu/nlp/rocstories/)]

[**A Corpus and Evaluation Framework for Deeper Understanding of Commonsense Stories**](https://arxiv.org/pdf/1604.01696.pdf)

Nasrin Mostafazadeh, Nathanael Chambers, Xiaodong He, Devi Parikh, Dhruv Batra, Lucy Vanderwende, Pushmeet Kohli, James Allen (NAACL'16)

Introduces a new dataset and task to test story understanding with commonsense knowledge. Given a premise document, a system is required to choose the most coherent ending from candidate endings. The dataset is a collection of everyday life stories, and captures causal and temporal commonsense relations between daily events.  
__

[**Reasoning with Heterogeneous Knowledge for Commonsense Machine Comprehension**](http://aclweb.org/anthology/D17-1216)

Hongyu Lin, Le Sun, Xianpei Han (EMNLP'17)

Divides the story cloze task into two steps: (1) mining various types of implicit knowledge that commonsense machine comprehension needs, and (2) reasoning the correct answer using the commonsense knowledge. Regarding (1), the paper defines commonsense knowledge as the association between two elements (events or entities), measured by the inference cost. They consider three types of association, event narrative coherence, entity coherence, and sentiment coherence. Regarding (2), given the commonsense inference rules obtained in (1), the paper computes the overall cost of transitioning from a given premise document to the possible endings by looking at the associations between individual phrases.  
__

[**The Effect of Different Writing Tasks on Linguistic Style: A Case Study of the ROC Story Cloze Task**](http://www.aclweb.org/anthology/K17-1004)

Roy Schwartz, Maarten Sap, Ioannis Konstas, Li Zilles, Yejin Choi, Noah A. Smith (CoNLL'17)

The authors discover that the majority of Story Cloze Tests (SCT) can be solved by just using stylistic features (e.g., sentence length) of the hypothesis text, without looking at the story content. This is because annotators adopt different writing styles when asked to write coherent vs. incoherent story endings. This work shows that when designing new NLP datasets and tasks, we need to pay special attention to the instructions given to annotators so that their writing styles will not be biased by desired labels.  
__

 [**Tackling the Story Ending Biases in The Story Cloze Test**](http://www.aclweb.org/anthology/P18-2119)

Rishi Sharma, James F. Allen, Omid Bakhshandeh, Nasrin Mostafazadeh
(ACL'18)

Designs new crowdsourcing schemes that overcome some of the writing style biases, and updates the SCT dataset. They propose two annotation methods: 1) asked annotators to keep a similar tone/sentiment for writing the "right" and "wrong" endings, and 2) asked annotators to modify the correct ending sentence to make a resulting story non-sensible.

***

### Children's Book Test (CBT) (Hill et al., 2016)

In the CBT cloze-style task a system is asked to read a children story context of 20 sentences. The following 21st sentence involves a placeholder token that the system needs to predict, by choosing from a given set of 10 candidate words from the document.      
__

[**Knowledgeable Reader: Enhancing Cloze-Style Reading Comprehension with External Commonsense Knowledge**](http://aclweb.org/anthology/P18-1076)

Todor Mihaylov and Anette Frank (ACL'18)

Works on the Common Nouns and Named Entities partitions of the Children’s Book Test. The paper proposes a neural reading comprehension model that integrates external commonsense knowledge represented as (subject, relation, object) --- e.g. (horse, [IsUsedfor], riding). The commonsense knowledge is mined from the Open Mind Common Sense part of ConceptNet. The neural model encodes not only the context document and the given question, but also the external knowledge tuples (analogous to attention mechanism), and then infers the answer to the question. This method of explicitly including external knowledge not only improves the performance but also provides evidence about the knowledge used to answer the question.



## Others
[**The winograd schema challenge**](https://www.aaai.org/ocs/index.php/KR/KR12/paper/view/4492/4924) (AAAI'15)

Consists of a sentence and a binary question about it, such as “The trophy doesn’t fit in the suitcase because it is too big. What is too big?”. The question involves a referential ambiguity that is resolved by commonsense knowledge.   

***

[**Is a 204 cm Man Tall or Small? Acquisition of Numerical Common Sense from the Web**](http://www.aclweb.org/anthology/P13-1038)

Katsuma Narisawa, Yotaro Watanabe, Junta Mizuno, Naoaki Okazaki, Kentaro Inui (ACL'13)

The motivation is to learn numerical commonsense in context. Specifically, the task is to infer whether a given number (e.g., three billion) is large, small, or normal for a given context (e.g., number of people facing a water shortage). The paper proposes two methods to obtain this type of knowledge from the web. The first technique learns the distribution of numbers co-occurring within a context, and infers whether a given value is large, small, or normal. The other technique uses textual clues used to express the judgment about values (e.g., "as much as"). For example, given an evidential sentence "He gave as much as $100 to a friend", we can infer that any amount larger than $100 in this context is considered large by commonsense.



## Application of Commonsense knowledge

[**Entity Commonsense Representation for Neural Abstractive Summarization**](https://arxiv.org/pdf/1806.05504.pdf)

Reinald Kim Amplayo, Seonjae Lim, Seung-won Hwang (NAACL'18)

Proposes to use entity commonsense (e.g. "Los Angeles Dodgers" and "New York Mets" are American baseball teams) to improve the coherence of summary generation. The entity commonsense is mined from Wikipedia.
