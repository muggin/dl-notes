## A Hierarchical Neural Autoencoder for Paragraphs and Documents     
_Authors:_ Jiwei Li, Minh-Thang Luong, Dan Jurafsky     
_Publishing Year:_  2015      
_Link:_ https://arxiv.org/abs/1506.01057     

#### Summary
The authors propose a neural architecture composed of LSTM units stacked in a hierarchy. The task presented in the publication was building an autoencoder capable of recreating long sequences of text, such as multiple sentences or entire documents. The true goal was to show that neural architectures are capable of generating coherent, semantically and syntactically correct sequences beyond trivial length (for general NLP tasks). The hierarchy of LSTM units arranges words, sentences and paragraphs into a hierarchical structure, with different levels of LSTM capturing compositionality on these different leveles of abstraction. The authors proposed a model called Hierarchical LSTM, which operated on two levels - words and sentences. The word-level Encoder processed tokens of sentences until it reached a `<sent-end>` token, the hidden state at that point was used as input in th higher-level sentence Encoder. The hidden state of the sentence-Encoder, after the `<doc-end>` token, was used as the starting point of the sentence-Decoder unit. The Decoder hierarchy worked in a analogous way, hidden state was passed from sentence-level to word-level Decoder, a single sentence was decoded and the word-level hidden state was used to progress the hidden state of the sentence-level Decoder. The authors also proposed an extension of this model utilizing Attention mechanisms on the sentence-level of abstraction.

#### Key points
- Dataset augmented with special tokens identifying end of sentences and end of documents
- Each of the abstraction levels has a dedicated LSTM encoding and decoding unit (4 units in total)

#### Experiments
- ROGUE and BLEU scores used for performance evaluation
- Experiments conducted on two datasets:
  - (TripAdvisor) HotelReview - BLEU 0.285, ROGUE-1 0.624 (w/ attention)
  - Wikipedia - BLEU 0.220, ROGUE-1 0.544 (w/ attention)
- Vocabulary was limited to 25k words, sequences limited to 250 words

#### Other notes
- Architecture a bit similar to multilayerd LSTMs , but the upper layers (higher abstraction) are not progressed with each token
