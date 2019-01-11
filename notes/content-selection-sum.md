## Content Selection in Deep Learning Models of Summarization
_Authors:_ Chris Kedzie, Kathleen McKeown, Hal Daume III   
_Publishing Year:_ 2018   
_Link:_ https://arxiv.org/abs/1810.12343

#### Summary
The authors carry out an analysis of SOTA architectures for summarization and their ability to select important content from the source documents.
The analysis looks into the encoding (sentence encoders) and extracting (sentence classifiers) parts of neural models.
SOTA models are compared with simpler architectures that were proposed by the authors in other to assess the benefits of complexity in the architecture.
Study was conducted on 6 datasets spanning several domains in order to achieve an unbiased picture of the field and its problems.


#### Key points
- Study conducted on different datasets and domains:
	- CNN/DM - news articles
	- NYT - news articles
	- DUC - single document summarization (small, high quality data)
	- AMI - staged office meetings
	- Reddit - personal stories shared on Reddit
	- PubMed - medical journal articles
- No advantage in using CNN/RNN models for sentence embedding compared to simple word embedding averaging
- No advantage in fine-tuning pre-trained embeddings (GloVe) used for initialization
- Sentence position is a significant feature on which models are dependent (mostly in news and journal article data)
- Models do not overly depend on POS of words in sentences
- Positions dependence of models must be broken, sentence embedding must be improved


#### Experiments
- Analysis of models conducted from different perspectives:
	- Depedence of the model on the sentence encoding component
	- Dependence of the model on the position of sentences (lead bias)
	- Depedence of the model on the POS of words in the sentences
	- Dependence of the model on the complexity of the architecture


#### Other notes
- Thorough analysis of the problem
- Great paper
