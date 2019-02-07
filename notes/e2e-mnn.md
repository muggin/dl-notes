## End-to-End Memory Networks
_Authors:_ Sainbayar Sukhbaatar, Arthur Szlam, Jason Weston, Rob Fergus   
_Publishing Year:_ 2015   
_Link:_ http://www.arxiv.org/pdf/1503.08895.pdf   

#### Summary
The authors propose a neural architecture with a recurrent attention model over a large external memory.
The model takes as input a passage of text and a query runs a fixed numbers of memory searches (hops) before returning an answer.
In each of the hops, the network embeds the input passage using two independent embedding matrices.
One version of the embbeded input is stored in the memory module and used together with the query for retrieval, the other is used later as an output from the memory module.
The embedded vectors stored in the memory are called memory cells, and the granularity of embedding (token or sentence level) depends on the specific use case.
The query passed as input to the model is also embedded using a third embedding matrix.
To retrieve the information, an inner product is computed between the embedded query and contents of the memory module and passed through a softmax function to obtain a soft distribution over the memory cells.
The output of the memory module is a weighted combination of the embedded input, where the weights come from the computed soft distribution.
The embedded query vector is element-wise added to the output from the memory module and used for prediction, or passed to the next memory hop.
The described procedure can be replicated multiple times, thus achieving a mechanism similar to recurrent attention.
The architecture is fully differentiable, which allows for end-to-end training without explicit supervision for the memory module.


#### Key points
- The memory network can be seen as an architecture with a recurrent attention mechanism over a large memory
- After each hop of the memory, the query vector is augmented with the retrieved information
- Each layer (hop) of the memory module has an independent set of three embedding matrices
- To reduce the number of parameters that must be learned, the embedding matrcies can be tied between memory hops
	- Adjecent tying - The input memory embedding matrix from the consecutive layer can be the same as the output embedding matrix from the current layer
	- Layer-wise (RNN-style) - Each layer of the memory network shares the same three embedding matrices
- Each memory hop consists of 3 phases:
	- Embedding the query (single matrix) and input passage (two matrices)
	- Computing the distribution over memory cells by a softmax normalized inner product between the query and memory cells
	- Computing the memory output as a weighted average of output memory embeddings, where the weights are the distribution from the previous step


#### Experiments
- Experiments conducted on a synthetic QA dataset and a Language Modeling task
- Performance of models improved with the number of hops of the memory unit (capped at 3)
- Performance does not beat traditional Memory networks with per-hop supervision


#### Other notes
- The End-to-End model is similar to the traditional Memory network with the difference that the standard model used a argmax function to return a single memory cell at each memory hop, instead of a weighted average of memory cell
- Due to the use of an argmax function in the traditional Memory network, each memory hop required separate supervision.
