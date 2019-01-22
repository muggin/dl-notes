## Deep Contextualized Word Representations
_Authors:_ Matthew Peters, Mark Neumann, Mohit Iyyer, Matt Gardner, Chris Clark, Kenton Lee, Luke Zettlemoyer   
_Publishing Year:_ 2018   
_Link:_ http://arxiv.org/abs/1808.08949   

#### Summary
The authors propse using a pre-trained deep, bidirectional Language Model to generate context dependent word embeddings.
Such embeddings are a function of the entire input sequence, not only single tokens.
Embeddings from Language Models (ELMo) are created by computing a weighted average of LM hidden states across all LM layers.
The authors claim that using information from intermediate layers of a biLM yields embeddings that are more information-rich.
To avoid the OOV problem, character-level n-gram embeddings are used as the initial embeddings layer.


#### Key points
- Contextualized embeddings represent both complex syntactic and semantic information (syntactic, semantic, polysemy)
- ELMo vectors are learned functions of internal hidden states of a 2 layer biLSTM LM:
	- Hidden states from intermediate layers are combined using weighted average
	- Hidden states from higher layers capture context-dependent semantics (good for word-level disambiguation, etc.)
	- Hidden states from lower layers capture complext syntactic aspects (good for POS tagging, etc.)
	- Weights of hidden states are learned on a per-task basis by the downstream model
	- Learned, per-task weighting of hidden states allows model to choose appropriate information from all layers
- ELMo omits the OOV problem by using CNN-based character-level n-gram embeddings before LSTM layers
- ELMo weights can be fine-tuned on domain specific data, or frozen and used as-is
- ELMo embeddings can be included at the bottom and intermediate layers of downstream models


#### Experiments
- Using hidden states from all layers outperforms using only top-layer states (CoVe)
- Using ELMo increases sample efficiency, downstream tasks can be trained faster/with less data


#### Other notes
