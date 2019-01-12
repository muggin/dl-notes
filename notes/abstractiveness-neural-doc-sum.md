## On the Abstractiveness of Neural Document Summarization
_Authors:_ Fanggang Zhang, Jin-ge Yao, Rui Yan   
_Publishing Year:_ 2018  
_Link:_ http://aclweb.org/anthology/D18-1089

#### Summary
The authors analyze and discuss the level of abstraction of popular text summarization algorithms tested on the CNN/DM dataset.
The paper proposes replacing abstractive models with a nearly-extractive approach, where the model relies only on copying mechanismsm.


#### Key points
- Abstractive models heavily rely on copying and attention when generating "novel" sequences
- Abstractive models have a extremely low level of abstraction, making them more extractive in nature
- The Generative component of models (softmax) is computationally and memory inefficient
- Summaries containing small text units from the input document have sufficient quality
- Removing the Generative part of a Pointer-Generator model (leaving only copying mechanisms) has several benefits:
	- Comparable performance on ROUGE and human evaluation
	- Cuts decoding time by 50% and GPU memory usage by 75%
	- Still allows the network to reorder the tokens copies from the input document


#### Other notes
- Short paper
