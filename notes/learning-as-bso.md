## Sequence-to-Sequence Learning as Beam-Search Optimization
_Authors:_ Sam Wiseman, Alexander M. Rush     
_Publishing Year:_ 2016   
_Link:_ https://arxiv.org/abs/1606.02960     

#### Summary
The authors propose a novel training procedure for sequence to sequence models that is based on the "Learning as Search Optimiztaion" framework. The goal is to address the known issues of the popular word-level cross-entropy training, which are: exposure bias (teacher forcing), loss-evaluation mismatch, label bias, discrepancy between training and test time decoding procedure. The main intuition is to use beam search decoding during training and to design a function that will penalize the model for letting the ground-truth sequence "fall off" a fixed sized beam during training. The authors used the Seq2Seq with Global Attention model ([Luong et al.](effective-approach-to-attention-nmt.md)) as their baseline. The first change is to abandon the probabilistic framework of the model and train the model using raw scores returned by the recurrent network. The authors also propose a training loss that penalizes the model in cases when the score of the ground-truth decoding beam is below that of the Kth highest beam (with an additional margin). On top of that, the loss is also scaled by a quality metric (such as BLEU) that allows to use sequence rather than word-leve costs during training. 

#### Key points
- Training procedure has two steps, forward pass and backward, just like with regular training
- In forward pass extend beams like with regular beam search as long as ground-truth is withing K highest scores
- In forward pass cut the beam and replace history with ground-truth prefix in cases where ground-truth falls of beam
- Caching partial results can improve performance of algorithm and keep it linear in the size of the sequence
- In backward pass, model is trained on groun-truth beam and partial beams that lead to loss violation
- Hard constraints can be added to the beam search successor function on a task-basis

#### Experiments
Experiments conducted on three tasks
- Word Ordering (PTB dataset) - BLEU 34.5
- Depedency Parsing (PTB dataset) - UAS/LAS - 91.57/87.26
- Machine Translation (IWSLT 2014 dataset) - BLEU 25.48

#### Other notes
