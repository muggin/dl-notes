## Plan, Attend, Generate: Char-Level Neural Machine Translation with Planning
_Authors:_ Caglar Gulcehre, Francis Dutil, Adam Trischler, Yoshua Bengio    
_Publishing Year:_ 2017    
_Link:_ https://arxiv.org/abs/1706.05087     

#### Summary
The authors propose extending an attention-based Encoder-Decoder architecture with planning mechanisms. The idea is to allow the model to plan its predictions ahead of time when it computes the alignments between the source and target sequences. The model creates an _alignment plan_ which is a matrix of future alignments, and a _commitment vector_ that decides whether the model should follow its plan or modify it. This mechanism allows the model to plan its predictions a few steps ahead, rather then doing ad-hoc decision at each step, this ability should allow it to generate more coherent translations. The general architecture of the solution was based on the model introduced by [Bahdanau et al.](jointly-learn-to-align-and-translate.md). The authors also proposed a reduced version of the model (that is cheaper computationally) that reuses the alignments from previous steps until the commitement vector decides that the plan should be modified. The model was trained jointly to minimize the negative log-likelihood.

#### Key points
- The proposed model is character-level to omit OOV/rare-word/spare-data problems
- The matrix of future alignments can be seen as an explicit plan of source-targe alignments at future time-steps
- The commitment vector decides whether the model should update the prediction plans or not
- The alignment plan is based on the prev hidden state, summary vectors, summary of the prev plan, and prev output
- If the model decides to modify the plan, each element of the alignment matrix is updated separately (gating)
- The reduced version of the model does not require to store the full alignment matrix over time
- To prevent the model to modifying/recomputing plan too often a loss penalizing this behavior was introduced

#### Experiments
- Trained on WMT '15 dataset - English-German
- Best BLEU score 22.83 points

#### Other notes
- Solution inspired by the Strategic Attentive Reader and Writer (STRAW) model
- How many steps ahead does the model plan, is it a hyperparameter?
- Humans plan what they want to say, and choose words ahead of time, this model tries to imitate that
- The model is similar to a basic attention-based Encoder-Decoder, but alignment weights (alphas) come from a precomputed matrix, and are not computed at each step
