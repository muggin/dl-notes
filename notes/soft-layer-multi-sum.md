## Soft Layer-Specific Multi-Task Summarization with Entailment and Question Generation
_Authors:_ Han Guo, Ramakanth Pasunuru, Mohit Bansal   
_Publishing Year:_ 2018   
_Link:_ https://arxiv.org/abs/1805.11004

#### Summary
The authors propose a soft, layer-specific multi-task approach to text summarization.
The auxiliary tasks in the learning procedure were question generation and entailment generation.
The base of the model was a Pointer-Generator network with coverage that was adapted to the multi-task setting, where both the Encoder and Decoder were partially shared between tasks.


#### Key points
- Improve text summarization training by adding auxiliary tasks:
	- Question generation - helps the model find salient parts of the input (based on the SQuAD)
	- Entailment generation - help the model generate summaries that entail the input article (based on SNLI)
- The Pointer-Generator network is extended to fit the layer-specific multi-task setting:
	- 2-layer Encoder - lower layer (syntactic) is task specific, upper layer (semantic) is shared
	- 2-layer Decoder - lower layer (generating) is task specific, upper layer (semantic) is shared
	- Attention between upper Encoder and Decoder layer is shared
- Parameters are shared using a soft-sharing strategy
- Before multi-task training, all models are pretrained up to 90% of convergance
- Multi-task training done in a round-robin fashion


#### Experiments
- Small (but consistent) improvements of the multi-task setting over baseline models
- Significant improvement in generalization (from CNNDM to DUC)


#### Other notes
- Badly written paper
