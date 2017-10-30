## Efficient Estimation of Word Representations in Vector Space
_Authors:_ Tomas Mikolov, Kai Chen, Greg Corrado, Jeffrey Dean  
_Publishing Year:_ 2013  
_Link:_ https://arxiv.org/abs/1301.3781

#### Summary
Authors propose two neural architectures, Word2Vec, for generating continous vector representations using large data sets.
The goals was to maximize the quality of the created vectors while minimizing the computational complexity of the models.
Both of the proposed models are simple, linear feedforward networks with hierarchical softmax as the output.
Training is done by running a sliding window through the corpus and using the center word and context words as training pairs.
The quality of the embeddings was primarily measured on the semantic similarity task.

#### Key points
- In other neural models most of the complexity comes from non-linear hidden layers and softmax output.
- Word2Vec architectures scale to data sets with billions of words an millions of words in vocabularies.
- Both models preserve the linear regularities between words.
- In both models the projection and output layer parameters are shared for all words.
- CBOW model predicts the target word given the context words as input.
    - Context words are projected to the vector space and averaged.
- Skip-gram model predicts the context words given the target word as input
    - At each step the number of context words (from past and future) is chosen randomly - dynamic context size.
- Output of models was a Hierarchical Softmax with the vocabulary organized as a Huffman binary tree.
    - Using Huffman tree decreases the computational complexity from log(V) (balanced binary tree) to log(unigram_perplexity(V)).

#### Experiments
- Trained on Google News data set - 6B tokens, 1M vocabulary
- Quality was measured on synactic and semantic similarity tasks
- After a certain point, increasing the size of the embedding vectors doesn't bring improvements
- Trained for 3 epochs using SGD with learning rate 0.025
- Skip-gram significantly outperforms CBOW on semantic similarity tasks
- New models outperforms previously used models in most tests

#### Other notes
- How exactly is the skip-gram model implemented? Is the context "flattened" to create separate (target, context_word) pairs?
