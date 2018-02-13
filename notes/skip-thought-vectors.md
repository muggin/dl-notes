## Skip-Thought Vectors
_Authors:_ Ryan Kiros, Yukun Zhu, Ruslan Salakhutdinov, Richard S. Zemel, Antonio Torralba, Raquel Urtasun, Sanja Fidler   
_Publishing Year:_ 2015   
_Link:_ https://arxiv.org/abs/1506.06726

#### Summary
The authors propose an approach for unsupervised learning of a generic, distributed sentence encoder. The technique, called _Skip-Thoughts Vectors_, is an generalization of _word2vec_ [skip-gram](dist-representation-words.md) model to the sentence level. The training objective of the model is to correctly generate context sentences `s_{t-1}`, `s_{t+1}`, given a target, middle sentence `s_t` as input. The idea is generic and can be used with any type of Encoder-Decoder architectures. Apart from the sentence encoding technique, the authors also propose a simple vocabulary expansion technique that allows to train the Encoder with a small vocabulary, unique 20k tokens, and expand it to a much larger vocabulary, unique 1M tokens.

#### Key points
- The experiments are conducted using an RNN Encoder-Decoder similar to the one proposed by [Cho et al.](learning-phrase-repr.md)
- The loss is a sum of log-probs for the "previous" and "next" sentences conditioned on the encoder representation
- The proposed training technique can be used with any sentence composition operator (encoder-decoder pair)
- The authors propose expanding the idea to larger contexts, entire paragraphs, or deeper architectures
- Vocabulary extension is made by a function that maps one (small) word embedding space to another (larger) one
- OOV words can have their embeddings mapped from the large space to the smaller space
- The large embedding space can be some pretrained model, such as _word2vec_ or _GloVe_

#### Experiments
- Model trained on the BookCorpus dataset (11k books, 74M sentences, 984M words)
- Sentence embeddings perform well on the SemaEval benchmark, but small distincition are sometimes missed
- Sentence embeddings were tested across 8 tasks and performed well on all - generic

#### Other notes
- Pretty obvious extension of _word2vec_ which yields very good empirical results
