# MSIF-NCP-BIRW
Implementation Code of MSIF-NCP-BIRW Model
# MSIF-NCP-BIRW

## 

**Type:** Package Title: A method for predicting the association between CircRNA and Disease based on Multi-source
information fusion through Network Consistency Projection and Bi-random walk

**Description:** This package implements the MSIF-NCP-BIRW algorithm, predicting circRNA-disease associations.

## Requirement

8GB memory
MATLAB R2017a or later

## 

## Calculate the cosine similarity matrix and integrate 

cosSim.m is used to calculate the cosine similarity of diseases and circRNA;
integratedsimilarity2.m is used to integrate disease similarity and circRNA similarity, respectively.
you should input the appropriate code in the matlab Command Window:

```
 [id ,il] = cosSim( interaction );                    % Return the processed cosine similarity matrix
 [sd,sl] = integratedsimilarity2(circSim,disSim,id,il,0.9);   % Integrated similarity for diseases and circRNAs
```

## Run MSIF-NCP-BIRW to infer potential associations between circRNAs and diseases

To analyze these data on MSIF-NCP-BIRW to further infer potential associations between circRNAs and diseases, you should input the appropriate code in the matlab Command Window:

```
%% Calculated scoring matrix
[NCP]=NCPHCDA(interaction,sd,sl);
%% result
allresult(disease,circRNA,interaction,NCP);
```

**NCPHCDA.m:** MSIF-NCP-BIRW core algorithm to predict potential circRNA-disease associations; it corresponds to the part of network  consistency projection in this paper.

**allresult.m:** the predicted results will be automatically saved in the excel table(allresult.xlsx)

## Cross validation

**NCPHCDALOOCV.m:** function Leave one for cross-validation. 

**pre_label_score_NCPHCDA.mat**the prediction score of Leave one for cross-validation.

**NCPHCDA5KCV.m:** function 5-fold cross-validation.

**pre_label_score_NCPHCDA_5kcv.mat**the prediction score of 5-fold cross-validation.

Running  NCPHCDALOOCV.m get the AUC value and ROC chart after implementing Leave one for cross-validation.

Running NCPHCDA5KCV.m get the AUC value and ROC chart after implementing 5-fold cross-validation.

