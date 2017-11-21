## GloVe: Global Vectors for Word Representations
_Authors:_ Jeffrey Pennington, Richard Socher, Christopher D. Manning   
_Publishing Year:_  2014   
_Link:_ https://nlp.stanford.edu/pubs/glove.pdf    

#### Summary
The authors propose a novel log bilinear regression model for creating vector representations of words. The model combines two of the major model families used for this task - global matrix factorization and local context window methods. The intuition behind the solution was to utilize the ratios of co-occurrence probabilities between pairs of tokens to find meaningful embeddings. The method first built a global coocurrence matrix, holding the statistics of the entire document, and later utilize it to encode pair-wise relations between words in a continuous vector space. The specific regression model was used in order to preserve the linear regularities between words in the vector space. To train the model the authors minimized the weighted sum of squared errors, where the weighting factor was used in order to minimize the noise introduced by very rare and popular tokens.

#### Key points
- By utilizing the global (co-occurrence) statistics the model is trained on each token pair only once (per epoch)
- Only non-zero entries in the co-occurrence matrix were utilized during training (non existing pairs were skipped)
- Weighting factor of the loss function parametrized by the co-occurrence count (inverted ReLU shape)
- Utilizing the global statistics of the corpus is advantageous for the models performance
- After training, the two weight matrices can be averaged to yield best results
- The GloVe model maps to other neural-based methods relatively well

#### Experiments
- Model tested on word analogy and similarity tasks
- Model trained on different corpora
  - 2010 Wikipedia - 1B tokens
  - 2014 Wikipedia - 1.6B tokens
  - Gigaword 5 - 4.3B tokens
  - Gigaword 5 + 2014 Wikipedia - 6B tokens
  - Common Crawl - 42B tokens
 - GloVe outperformed other models in most tests
 - Best results on Common Crawl corpus with 300-dim embeddings

#### Other notes
- Authors claim that they reimplemented Word2Vec and achieved better results than the original author
