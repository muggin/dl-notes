## Abstractive Text Summarization using Sequence-to-sequence RNNs and Beyond
_Authors:_ Ramesh Nallapati, Bowen Zhou, Cicero dos Santos, Caglar Gulcehre, Bing Xiang      
_Publishing Year:_ 2016     
_Link:_ https://arxiv.org/abs/1602.06023     

#### Summary
In the paper the authors apply an attention-based Encoder-Decoder network designed for Machine Translation to the problem of Abstractive Text Summarization and treat it as the baseline for experiments. The architecture is also extended in several ways to address the differences between the NMT and ATS tasks and shortcomings of the Neural Language Modeling. The problems which are considered where: large output size of the vocabulary, caputing kewywords, unseen and rare words, hierarchical structure of sentences. To solve the first problem, the authors use the Large Vocabulary (LVT) trick, the decoder-vocabulary is limited to only the words present in the batch (topped by words from regular vocabulary until a fixed size is reached). The second problem is solved by extending the regular word-embedding word representation with additional information containing linguistic features. The third problem is solved by adding Pointing mechanisms. The last problem is solved using hierarchical attention, working on word and sentence level. In addition to the complex model, the authors also introduce a new dataset specifically designed for the task of Abstractive Text Summarization with summaries longer than a single sentence. The new dataset is a modification of the CNN/DailyMail datasets introduced by [Hermann et al](teaching-machines-read.md).

#### Key points
- Encoder used a bi-directional GRU unit, Decoder used a uni-directional GRU unit
- Output vocabulary dynamically created based on the vocabulary of the current batch (and sampled if too small)
- Benefit of LVT is that the softmax becomes less of a computational bottleneck
- Word embeddings extended with POS tags, Named Entity tags, TF, IDF and other word statistics
- External switching mechanisms used that decided whether next token should be generated or copied from input
- Hierarchical attention was used to attend on different levels of abstraction (word and sentence level)
- Word level attention weights are rescaled using sentence level attention weights before computing context vector

#### Experiments
- SoTA results on DUC 2003 and 2004 corpora
- SoTA results on the new CNN/DailyMail corpus
- Model with all extensions took 18 days to train on a single K40

#### Other notes
- This paper seems to survey the field of NLP and incorporate all the developments into a single model
