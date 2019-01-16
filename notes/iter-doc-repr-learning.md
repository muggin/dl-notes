## Iterative Document Representation Learning Towards Summarization with Polishing
_Authors:_ Xiuying Chen, Shen Gao, Chongyang Tao, Yan Song, Dongyan Zhao, Rui Yan    
_Publishing Year:_ 2018   
_Link:_ https://arxiv.org/abs/1809.10324  

#### Summary
The authors propose an iteration-based extractive model for text summarization.
The intuition behind the model is to refine the representation of the input document in an iterative fashion, so that more relevant information can be used to choose sentences for extraction.
The model contains separate encoder, iterative, and decoder units for each iteration, where the number of iterations is fixed before training.
The encoder also contains selective-reading mechanisms, similar to _global information filters_, that modify the sentence representation based on the full-document vector.
Based on the outputs from the model, input sentences are ranked, and the top _k_ sentences (in that order) are considered to be the summary.


#### Key points
- Encoder, Iterative, Decoder units repeated per iteration
- Encoder unit: 
	- Positional sentence encoder
	- BiGRU sentence encoder
	- Selective-reading mechanism for filtering sentence embeddings according to full-document representation
	- Returns all sentence embeddings (for Decoder), and last refined sentence embedding for iterative unit
- Iterative unit:
	- Updates (polishes?) the full-document representation
	- Returns the document representation based on last sentence embedding from current iteration and document represntation from previous iteration
- Decoder unit:
	- BiGRU layer that returns hidden representations based on sentence and document representations
- Sentence Labeling unit:
	- Outputs the labels for each sentence of the input article
	- Predicts labels based on concatenated hidden states from all previous iterations


#### Experiments
- Certain improvements on ROUGE metric over baseline models (short summaries ~75 words)
- Very small improvements on ROUGE metric over baseline models (long summaries ~275 words))


#### Other notes
- Not enought details given for certain parts of the work
- What "unsupervised" algorithm used to obtain labels for supervision during training
- Very complex architecture
