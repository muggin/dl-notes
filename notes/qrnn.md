## Quasi-Recurrent Neural Networks
_Authors:_ James Bradbury, Stephen Merity, Caiming Xiong, Richard Socher      
_Publishing Year:_  2016    
_Link:_ https://arxiv.org/abs/1611.01576    

#### Summary
The paper introduces a novel neural architecture for sequence modeling that improves the overall parallelism of the model. The motivation of the work was to improve on the drawbacks of RNN and CNN architectures applied to NLP tasks. The authors propose an architecture similar to a gated recurrent unit, such as LSTM or GRU, using convolutional components. Each QRNN layer consists of two subcomponents that are analogous to convolutional and pooling layers in CNNs. The convolutional subcomponent performs computations on the input across timesteps thus "combining" short-term information across time. The pooling subcomponent performs convolutions on the input with separately trained filter banks and uses the results as gating mechanisms on the output of the convolutional subcomponent, this allows modeling long-term dependencies. The output of the pooling layer is treated as the output of the QRNN layer. The architecture can be further extended with different mechanisms that are known to improve performance of RNN and CNNs, such as Dropout, attention, densly connected layers, etc.

#### Key points
- Convolutional subcomponent can be applied in parallel across time
- Pooling subcomponent can be applied in parallel across features (sequential computation)
- Convolutional layers uses masked convolution to prevent involvment of information from future timesteps
- Three different pooling layers were proposed that allow to emulate different gating mechanisms:
  - _f_ - future state (in time) computed based on prev state and input only using forget gate
  - _fo_ - future state computed based on prev state and input using forget and output gate
  - _ifo_ - future state computed based on prev state and input using forget, input and output gate
- Variational-inference based dropout and zoneout can be used for regularization
- Architecture can be extended to an Encoder-Decoder model

#### Experiments
- Speedups from 1.4x to 16.9x compared to optimized cuDNN LSTM


#### Other notes
- QRNN based models have better predictive accuracy than LSTM-based models of equal hidden-size
