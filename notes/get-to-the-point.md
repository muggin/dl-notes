## Get To The Point: Summarization with Pointer-Generator Networks 
_Authors:_ Abigail See, Peter Liu, Christopher Manning   
_Publishing Year:_ 2017     
_Link:_ https://arxiv.org/abs/1704.04368

#### Summary
The authors propose a novel architecture for Abstactive Text Summarization which is based on the attention Encoder-Decoder. The base architecture is extended in two orthogonal ways, by adding a pointing mechanism and by using coverage vectors. The extension where designed with the goal to enable the model to generated complex, multi-sentence summaries. The pointing mechanism allows the model to choose whether the next token should be generated using a Softmax output or copied from the input sequence. The coverage vector allows the model to track which parts of the input sequence (document) where already covered in the generated summary, thus prevent from repetition. 

#### Key points
- Coverage vector is a sum of attention distributions over all previous timesteps
- Coverage vector shows the degree of coverage each part of the input received from the attention mechanism
- Loss function is augmented with a coverage penalty, penalizing the network for focus too much on certain parts
- Pointer mechanisms used external, learned, switch that decided whether to copy or generate

#### Experiments
- Experiments conducted on CNN/DailyMail dataset as proposed by [Nallapati et al.](abstractive-text-sum-rnns-beyond.md)
- Experiments showed that the pointer mechanism causes the model to return less novel (abstractive) sentences
- Coverage mechanism added after initial phase of training, otherwise lowered performance of model

#### Other notes
- Not sure why authors claim the switchable pointing mechanism to be novel since it was introduced in a few articles before
