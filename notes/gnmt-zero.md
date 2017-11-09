### Google's Multilingual Neural Machine Translation System: Enabling Zero-Shot Translation
_Authors:_ Melvin Johnson, Mike Schuster, Quov Le, Maxim Krikun, Yonghui Wu, Zhifeng Chen, Nikhil Thorat    
_Publishing Year:_ 2016   
_Link:_ http://arxiv.org/pdf/1611.04558.pdf  

#### Summary
The authors propose a solution that allows to use a single NMT system to translate between multiple different languages. The solution requires not changes to the standard Encoder-Decoder architecture of the NMT models. To indicate the target lanuage of translation a single artificial token (`<2[lang-code]>`) is prepended to the source sequence (this is the only change!). Similarly to the [GNMT](gnmt.md) paper, the model uses a vocabulary consisting of sub-word units (wordpieces) that are shared across languages.

#### Key points
- Training on all available languages at the same time (sequence pairs sampled from data at each training step)
- More languages can be added by simply retraining the model on new data
- Languages with little data available gain from training together with languages with lots of data
- Model automatically learned zero-shot translation (translate between language pairs not present in the data)
- Sharing model parameters between all languages forces the model to generalize across language boundaries
- Sharing wordpieces allows handling multiple languages with a single model without increasing its number of params

#### Experiments
- Three types of experiments conducted:
  - many source languages to one target language
  - one source language to many target languages
  - many source languages to many source languages
- Model trained on WMT' 14 and Google's internal translation data sets
- Visual inspection gave evidence for an interlingua representation
