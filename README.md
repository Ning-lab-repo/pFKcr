# pFKcr
Prediction of Functional Lysine (K) Crotonylation (pFKcr) Sites

We developed a novel protein language model (PLM)-based framework called "prediction of Functional Kcr sites" (pFKhib). This framework captures intricate patterns in protein sequences, enabling more accurate and efficient predictions of functional Kcr sites. In this study, we defined the crotonylation site peptide (CSP) as a crotonylation residue with m residues upstream and n residues downstream, using CSP (10, 10) for training. First, we trained a pre-trained model, pFKcr-pre. The CSP (10, 10) peptide was encoded into 11 types of 1D feature vectors, with each vector associated with a specific deep neural network (DNN) model to predict a score. This approach generated 11 scores for each Kcr site. We then employed an integrated DNN to combine these scores into a final prediction score. Finally, we fine-tuned the pFKcr-pre model through few-shot transfer learning to develop the pFKcr model, which predicts the functionality of Kcr sites.
# Requirements
The main requirements are listed below:

* Python 3.8
* Numpy
* Scikit-Learn
* matplotlib
* Keras
* Pandas
# The description of the pFKhib source
* after_cd_hit.ipynb
  
  The code is used for turning FASTA format sequences after being deredundant by CD-HIT into CSP (10,10) peptides.
* encoding_10features.ipynb
  
  The code is used for encoding a CSP (10,10) peptide into 10 kinds of 1D feature vectors (PseAAC, CKSAAP, OBC, AAindex, ACF, GPS, PSSM, ASA, SS, and BTA) for DNN training.
* transformer.ipynb
  
  The code is used for training the transformer model to generate the 11th feature vector, also named transformer.
* transformer_feature.ipynb
  
  The code is utilizing the transformer trained above for encoding a CSP (10, 10) peptide into a 128D feature vector which is also named transformer.
* DNN.ipynb
  
  The code is 11 fully connected neural network frameworks of 11 types of featurese for model pre-training. Pre-training is applied to predict whether a lysine site is a crotonylation site.
* integrated_DNN.ipynb
  
  The code is a fully connected neural network framework that can summarize the 11 scores and make a final prediction for model training and evaluation. Integrated_DNN will not participate in transfer learning.
* transfer_learning.ipynb
  
  The code is for 11 DNNs' transfer learning to apply these DNNs to predict whether a Kcr site is functional.
* predict.ipynb
  
  The code is to use pFKcr containing 11 DNNs and the integrated DNN we mentioned above to use 11 features generated from a group of CSP (10, 10) peptides (Kcr sites) to score them and predict whether each of them is functional.

* ROC.py
  
  The code is used to draw 11 ROC curves of the pFKcr model consisting of 11 parallel DNNs and integrated DNN.
