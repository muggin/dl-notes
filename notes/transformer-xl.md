## Transformer-XL: Attentive Language Models Beyond a Fixed-Length Context
_Authors:_ Zihang Dai, Zhilin Yang, Yiming Yang, Jaime Carbonell, Quoc Le, Ruslan Salakhutdinov   
_Publishing Year:_ 2019   
_Link:_ http://arxiv.org/abs/1901.02860   

#### Summary
The authors propose a novel Transformer-based architecture for language modeling that allows passing dependencies beyond a fixed-length context.
The Transformer-LM works by taking fixed-sized segments of context as input and predicting the next token in the sequence.
Propagating dependencies beyond the fixed-sized segment was achieved by introducing a segment-level recurrence mechanism.
Hidden states from the previous segment are frozen, cached, and concatenated with hidden states from the current segment before applying self-attention.
Reusing hidden states creates a connection between current and previous segments, and allows the model to exploit information from the history.
In order to keep the positional information coherent when reusing hidden states the authors propose using _relative positional encodings_.


#### Key points
- Standard Transformer-LM processes fixed-sized segments without information flow between segments:
	- The largest possible dependency length is upper bounded by the segment length
	- Segments are not semantically bounded which causes the model to operate with less contextual information
- Hidden states from previous segment are only used when computing the Key and Value inputs of self-attention
- Dependencies between current layer and past layers shift downward per-segments
- The largest dependency grows linearly w.r.t. the number of layers and the segment length
- Gradients are not passed to reused hidden states
- Reusing hidden states improves the speed of inference by not recomputing hidden states
- During inference, more segments can be reused (limited by GPU memory)
- Using absolute position encoding within a segment doesn't allow the model to destinguish between inputs from consecutive segments
- Relative Positional Encoding allow to keep position information coherent between segments:
    - Create an embedding matrix of relative distances
    - Are injected in the attention score instead of being added to the input embeddings/hidden states
- The recurrsive mechiansm and relative positional encoding together offer the full solution


#### Experiments
- Improve SOTA on several char/word-level benchmarks
- 12 and 24 layers models offer performance improvements
- Transformer-XL offers 1800x speed-up over Transformer-LM when using 3800 token attention


#### Other notes
- Auxiliary losses where not necessary to train model
