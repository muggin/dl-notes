## Distilling the Knowledge in a Neural Network
_Authors:_ Geoffrey Hinton, Oriol Vinyals, Jeff Dean   
_Publishing Year:_ 2015   
_Link:_ https://arxiv.org/abs/1503.02531   

#### Summary
Authors propsed means of transferring knowledge from large models or ensembles of models into single, smaller networks.
In the distillation process, the small model is trained to recreate temperature-smoothened softmax outputs of the larger model. 
If target labels are available, the knowledge transfer process can be improved by an auxiliary task where the small model also predicts hard classes.
The authors also propse a method of training ensembles on very big datasets, where the main model is augmented with specialist models that handle subsets of mostl commonly confused classes.


#### Key points
- Large models used to extract structure from data during training, smaller models using _distilled_ knowledge used for inference
- Relative probabilities over all classes output by a large model contain valuable information about the generalization abilities of the model
- Training smaller models to mimic the logits of larger models is a special, inferior case of _distillation_
- The distilled model is taught to generalize in the same fashion as the large model
- Model distillation uses the output softmax of the larger model with a temperature factor to obtain smoother distributions
- Auxiliary loss can be added so the small model matches both the soft target from the large model and the hard targets from the data labels
- Training ensembles of specialists:
	- General model is trained on the entire dataset until convergence
	- Specialist models are created to handle sets of confused classes
	- Specialist models are copies of the general model with pre-trained weights
	- Subsets of confused classes are found using clusterin algorithms on the confusion matrix of the general model
	- Specialists are fine-tuned on data enriched with confused classes
	- Classes of specialist models can overlap
	- Training of specialists can be parallelized, in contrast to mixture-of-experts models


#### Experiments
- MNIST data - small increase in test error in comparison to the large model
- Speech data - small decrease in test frame accuracy, no change in WET in comparison to the large model
