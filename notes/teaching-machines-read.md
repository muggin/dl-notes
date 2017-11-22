## Teaching Machines to Read and Comprehend
_Authors:_ Karl Hermann, Tomas Kicisky, Edward Grefenstette, Lesse Espeholt, Will Kay, Mustafa Suleyman, Phill Blunsom     
_Publishing Year:_ 2015      
_Link:_ https://arxiv.org/abs/1506.03340     

#### Summary
The authors came up with a novel, automated methodology of creating large-scale datasets for training and testing Machine Reading/Comprehension models. The main intuition behind the idea is that the performance of such models can be evaluated by checking their ability to answer question that are based on the content present in the text they read. The algorithm is given a set of documents together with related summaries, and translates them into (document, question, answer) tripples, where the question and answer is generated from the summary. Datasets in such form allow training of models in a supervised fashion. Apart from the data creation algorithm, the authors also proposed three neural models for the mentioned task. The general framework was to have a embeddings matrix of the vocabulary and a neural models that summarize the document and query into a single vector, the answer was retrieved by the similarity between the embeddings and the summary vector. The first model, Deep LSTM Reader, was a simple multilayer-LSTM. The second and third model, called Attentive Reader and Impatient Reader, extended the architecture with attention mechanisms.

#### Key points
- Document summaries should not contain sentences directly copied from the documents (abstractive summaries)
- Processing summaries into query/answer pairs is based on Entity Recognition algorithms
- Entities in documents/summaries were anonymized to prevent models from using external knowledge sources
- Authors created two datasets - DailyMail and CNN (now used to train text summarization and QA models)
- Incorporating attention mechanisms in Machine Reading models is CRUTIAL for their good performance

#### Experiments
- Experiments performed on the CNN/DailyMail datasets
- Neural models outperformed all other baseline models
- Attentive and Imaptient Reader outperformed LSTM-only neural models
