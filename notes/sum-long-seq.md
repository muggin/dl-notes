## Generating Wikipedia by Summarizing Long Sequences
_Authors:_ Peter Liu, Mohammad Saleh, Etienne Pot, Ben Goodrich, Ryan Seppasi, Lukasz Kaiser, Noam Shazeer    
_Publishing Year:_ 2018   
_Link:_ https://arxiv.org/abs/1801.10198   

#### Summary
The authors approach the problem of generating long texts (Wikipedia articles) from the perspective of abstractive, multi-document summarization.
Given the topic of the article and related documents the generative process is conducted in two stages.
First, an extractive algorithm finds salients parts of the input documents, next an abstractive neural decoder generates a text passage conditioned on the article topics and previously retrieved information.
The abractive decoder used in the paper was based on the Transformer decoder architecture.
The paper also introduced a new dataset (WikiSum) for multi-document summarization based on Wikipedia article leads (outputs) and referenced documents and web searches (inputs).


#### Key points
- Benefits of proposed WikiSum dataset:
	- Order of magnitude larger than CNN/DM
	- Target summaries are significantly more abstractive than in CNN/DM
	- Target summaries (article leads) followo Wikipedia style manuals
	- Data from different sources - Article citations and Google search results
- Extractive algorithms find salient paragraphs of input documents by ranking:
	- Identity - using first L tokens of input documents
	- TF-IDF - article topic treated as the query, paragraphs as documents
	- TextRank - PageRank is run on graph where nodes are paragraphs and edges are word overlaps
	- SumBasic - sentence scores are computed based on word frequences
- Article topic is concatenated with salient paragraphs and fed as input to Decoder
- Encoder-Decoder architecture replaced with (customized) Transformer Decoder
- Models inputs and outputs are separated with special token and used as input sequence for training
- Model trained as standard language model - given input predicts the next token
- Words tokenized to sub-word chunks
- Enhanced self-attention layers for better memory performance:
	- Local attention - computing attention within 256-token blocks)
	- Memory-compressed attention - number of key/values is reduced by using a strided convolution layer



#### Other notes
- Data-driven information extraction might work better than TF-IDF and other tested algorithms
- Questions for human evaluators: Grammaticality, Redundancy, Referential clarity, Focus, Structure, and Coherence
