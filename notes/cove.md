## Learned in Translation: Contextualized Word Vectors
_Authors:_ Bryan McCann, James Bradbury, Caiming Xiong, Richard Socher   
_Publishing Year:_ 2017  
_Link:_ http://arxiv.org/abs/1708.00107   

#### Summary
The authors propse using a pre-trained LSTM-based Encoder to create contextualized word embeddings that should improve performance of downstream NLP models.
Context vectors (CoVe) are created by passing standard word embeddings (Word2Vec, GloVe, etc.) through a biLSTM and utilizing its hidden states as the new representation.
The Encoder is pre-trained as part of a seq2seq, attention-based NMT systems, trained on English-German data.
Intuitively, NMT is a good task for pre-training because the encoding part of the model must embed all relevant information in its hidden states that will allow the decoder to generate an exact translation of the source text.
The authors show that simply concatenating CoVe vectors with basic word embeddings significantly improves performance of downstream models.


#### Key points
- The NMT Encoder utilized a standard, two-layer biLSTM unit
- LSTM hidden states from last layers are used as CoVe embeddings, both directions are concatenated
- Context vectors concatenated with word embeddings significantly improve performance of downstream models
- Quanitity of training data is positively correlated with the performance of CoVe embeddings on downstream tasks


#### Experiments
- Downstream model performance improves on all tasks: sentiment classification, question classification, entailment, question answering
- Using CoVe embeddings pushes downstream model to achieve SOTA on SNLI and SST
- Combining word embeddings, n-gram embeddings, and CoVe further improves downstream performance
