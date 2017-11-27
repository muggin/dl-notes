## Pointer Sentinel Mixture Model
_Authors:_ Stephen Merity, Caiming Xiong, James Bradbury, Richard Socher    
_Publishing Year:_ 2016    
_Link:_ https://arxiv.org/abs/1609.07843    

#### Summary
The authors propose a neural architecture for modeling sequences. The model is a combination of a standard RNN network with a softmax output over a fixed vocabulary, and a Pointer Network with a softmax output over the vocabulary present in the seen input sequence. The intuition is to handle the OoV/rare-word problem by extending the fixed output vocabulary, with a dynamic vocabulary dependent/based on the previously seen parts of text. The architecture is very similar to that proposed by [Gulcehre et al.](pointing-the-unknown.md), and two major changes were proposed. Firstly, instead of using the raw hidden state of the Decoder to compute the attention weights, the authors create a _query vector_ by applying a non-linear transformation to the hidden state and use it to compute the attention. Secondly, instead of using a "switching network" that decided which of the outputs to use, the authors augment the sequence of hidden states (annotations) with an additional vector called the "Sentinel". In cases where the Pointer Network is unsure where to point it can place the probability mass on the Sentinel, which means that the output of the regular softmax should be used. The final distribution over the vocabulary is computed as a mixture of the distribution of the Pointer Network and the regular Softmax output with the probability of the sentinel (g) being the mixing component. Apart from the architecture, the authors also created a new dataset _WikiText_ designed as a benchmark for Language Modeling.

#### Key points
- Pointer network creates a distribution over seen words (not over positions) - same words have merged probs.
- The values of the _sentinel vector_ are learned during training
- The pointer network attends only a fixed window of the seen sequence (size chosen as hyperparameter)
- The setup encourages the two models to compete - use pointer whenever possible and back-off to standard model when necessary

#### Experiments
- Experiments made on two datasets
  - PTB (900k training tokens) - 70.9 test perplexity
  - WikiText-2 (2M training tokens) - 80.8 test perplexity
- The authors also created a mid-sized corpus called WikiText-103 (103M training tokens)

#### Other notes
- Authors decided to test the new network on Language Modeling, instead of machine translation or text summarization, why?
