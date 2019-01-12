## Improving Neural Abstractive Document Summarization with Explicit Information Selection Modeling
_Authors:_ Wei Li, Xinyan Xiao, Yajuan Lyu, Yuanzhuo Wang   
_Publishing Year:_ 2018   
_Link:_ http://aclweb.org/anthology/D18-1205

#### Summary
This work proposes extending summarization models with explicit information selection mechanisms.
The basic encoder-decoder architecture is augmented with an information selection layer that explicitly finds the salient parts of the summarized article.
Information selection is done in two phases, first sentence-embeddings are filtered using a gated global information filter.
Next, for each generated sentence, local sentence selection is conducted that helps choose the sentences that should be paraphrased.
The information extraction process is further enforced during training by a distant-supervision loss.


#### Key points
- Abstractive text summarization can benefit from explicit information selection
- Text summarization can be seen as a three phase task:
    - Document encoding - encoding words and sentences into vector representation
    - Information selection - filtering and choosing salient parts of the input
    - Summary decoding - paraphrasing the salient parts into a coherent output
- Generate the summary sequentially, one sentence at a time
- Explicit information selection mechanism:
    - Gated Global Information Filtering - use document embedding (last hidden state of sentence-embedding RNN) with gating mechanisms to filter sentence embeddings from irrelevant information
    - Local Sentence Selection - select salient and relevant sentences (using attention-like mechanism) from the document that will be paraphrased in a given step (set decoder hidden state to weighted average of chosen sentences)
- Decoder uses attention over input words, attenion scores scaled by Local Sentence Selection weights
- Distant supervision of information selection:
    - Add loss term that is the KL-divergence between Local Sentence Selection distribution and artificial target distribution
    - Target distribution computed as the cosine distance between a reference-summary sentence and all source document sentences
- Hierarchical Beam Search used for decoding


#### Experiments
- Ablation study shows significant performance drop when removing any of the proposed parts
- Slightly outperforms baseline models according to a human evaluation study
- Significantly outperforms baseline models when generating long summaries (> 125)


#### Other notes
- Visualization of sentence selection vector shows heavy focus on the leading sentences (lead bias)
