## Distributed Representations of Words and Phrases and their Compositionality
_Authors:_ Tomas Mikolov, Ilya Sutskever, Kai Chen, Greg Corrado, Jeffrey Dean    
_Publishing Year:_ 2013   
_Link:_ https://arxiv.org/abs/1310.4546    

#### Summary
The authors propose improvements to the skip-gram Word2Vec model introduced by [Mikolov et al.](notes/efficient-esti-of-word-repr.md). The old objective function that utilized hierarchical Softmax was replaced with Negative Sampling with the intention to improve the training speed. Apart from changing the training procedure, the authors also proposed a vocabulary subsampling technique that lowers the negative impact of very popular words on the quality of embeddings. The paper also suggests how to build semantically meaningful representations for multi-word phrases.

#### Key points
- In negative sampling the gradient is computed for all "positive" (target) labels and only for a small sample of "negative" (incorrect) labels.
- To build embeddings for phrases the phrase should be treated as a single token in the vocabulary
- The subsampling function heavily penalizes words that have an occurrence frequency above a certain threshold
- Training the skip-gram model does not involve multiplying dense matrices
- Created embeddings exhibit linear structure, analogical reasoning can be performed using vector arithmetic

#### Experiments
- Trained on an internal Google dataset - 1B tokens
