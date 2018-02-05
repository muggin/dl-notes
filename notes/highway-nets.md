## Highway Networks
_Authors:_ Rupesh Kumar Srivastava, Klaus Greff, Jurgen Schmidhuber     
_Publishing Year:_ 2015    
_Link:_ https://arxiv.org/abs/1505.00387    

#### Summary
The authors propose a new architecture designed to ease gradient-based training of very deep networks. The architecture uses a gating mechanism, `Transform Gate`, that allows free and unhindered flow of information across multiple layers of a network. The intuition is to allow the network to choose (based on the current input) when and to what extent use specific layers of a network. Depending on the output of the Transform Gate, the behavior of a Highway Layer can vary between a "plain" layer and a layer that simple passes inputs through. The Highway paths also allow the gradients to flow back freely. The idea of using gating mechanisms to control the flow of information was inspired by gating mechanisms known in RNN unit (LSTM, GRU).

#### Key points
- Highway layer uses gating to split signal across 'regular' layer and passing inputs through
- Highway layer: `y = T(x) * f(x) + (1 - T(x)) * x`, where `T` is the `Transformer` and `f` is the regular layer
- For deep networks bias of Transform Gate should be initalized to negative vaules to encouragee _carry_ behaviour

#### Experiments
- Experiments showed that Highway layers can help train models up to 900 layers deep
- Significant improvement in convergence for networks larger than 10 layers

#### Other notes
- Idea is very similar to Residual connections. Instead of having two paths (ResNet) through which information flows in parallel in an ungated manner, Highway connections use gating mechanism that splits how much of the signal will go through each path.
