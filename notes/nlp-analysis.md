## Analysis Methods in Neural Language Processing: A Survey
_Authors:_ Y. Belinkov, J. Glass   
_Publishing Year:_ 2018   
_Link:_ https://arxiv.org/abs/1812.08951   

#### Summary
The authors describe methods of analyzing neural networks when applied to problems in natural language processing.
The works reviews different groups of analysis tools: 
inspecting the linguistic information captured by neural models,
visualization methods, 
challenge sets and test suites, 
adversarial examples, 
explaining model predictions, 
and other methods.


#### Key points
- Linguistic information captured by models:
	- Associating network components with linguistic properties by predicting those properties from network activations (using auxilary classifier with inputs from analyzed model)
	- Computing correlation between activations and linguistic properties (RNN state vs. depth in syntax tree)
	- Computing correlation between attention weights and linguistic properties
- Visualization:
	- Showing RNN hidden unit activations (and their correspondence to grammatical structures)
	- Attention alignments showing alignments between sequences
	- Clustering and visualizing network activations in comparison to linguistic properties
	- Computing saliency measures that match predictions with input features
- Challenge sets:
	- Data sets that evaluate models ability to handle specific linguistic phenomena
	- In comparison to regular test sets that measure the performance in the average case, challenge sets stress test models
	- Data sets are usually small in size and manually created (f.e. embeddings similarity of rare words or verbs)
- Adversarial examples:
	- Finding similar examples that cause dramatically different predictions from the models
	- Generating adversarial examples by common text edit operations (character- or word-level)
- Explaining predictions:
	- Correlating fragments of the input with model predictions
- Other methods:
	- Masking and erasing certain networks components and correlating the changes with model outputs.


#### Other notes
- Paper conclusions:
	- Little discussion about the link between tasks of auxiliary classifiers and original tasks
	- Little work done on explaining predictions of neural models
	- More challenge sets are needed (outside of NLI/MT tasks)
	- Analysis methods outside of English are limited
