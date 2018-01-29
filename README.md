# Summer_Internship_2017 Machine learning based model to predict ligand binding affinity 
It is the Repository of the project during my sophomore year summer internship. Overview...docx headlines the project idea and Source of data collection. Data curation and Feature extraction is expained in Pre.docx.Different Factor analysis models and algorithmic details are explained in Dimensionality reduction docx.

# Project Topic
Statistical model to predict the binding affinity of a ligand towards a receptor(protein sequence).


# Data collection
A data set comprising the bioactivity data of compounds tested against the nuclear receptor protein family was compiled from the ChEMBL database, release number 23 (updated May 2017). Particularly, this encompassed the compilation of a total of 23 member proteins belonging to the nuclear receptor protein family.

Ligand binding and steroid binding domain sequences of each protein are retrieved from Uniprot web server release 2017_07. The binding site can be confirmed by structure visualization in Pymol.   


# Fingerprint/Descriptor(Feature EXtraction) generation for ligand and receptor 
      
Data collected from CHEMBL contains three columns –“ COMPOUD_ID” ,”PROTEIN_ID”,”COMPOUND’S SMILE FORMULLA “,”IC-50” value.

Compound’s smile (CNCCOOH etc.) is needed to be converted in to numeric vector format to make it understandable to the algorithms.


Different strategy’s and algorithms are available  i.e. – EstateFingerprinter,
GraphOnlyFingerprinter, MACCSFingerprinter, SubstructureFingerprintCount, AtomPairs2DFingerprintCount etc.

# Pre-processing and data preparation for proteins

Since proteins have ligand as well as steroid binding site ,our first step was to only select the sequence responsible for ligand binding .

Molecular fingerprint of protein sequence was calculated from the uniport web server which creates the descriptors depending on the sequence of bases (Adenine , Guanine ,Cytosine ,Thiamine).


# Dimensionality reduction and Algorithmic steps 

After the feature extraction step , we have feature vector of each ligand compound and it’s target protein. Different approaches have been tested to combine the feature vector of ligand and protein  to produce a single combined feature vector (This feature vector should represent the interaction of ligand with the protein).

The best combination of feature vectors was found to be component wise product of compound’s feature vector and receptor feature vector producing a vector of n*m size for each compound and target pair.



# Dimensionality Reduction techniques

Partial least square method to reduce the dimension was found to be more better than the PCA .Since Partial least square find the components such that the variance w.r.t. predictor variables as well as the target variable is minimized.

# Results 
After Factor analysis on the feature matrix five components were selected and different algorithms were tried.

Results on 5 fold cross Validation of training data 

1. Linear regression on Components obtained by PCA – average precision score – 0.62

2. Bagging based approach -
    
 Random forest on  Components obtained by PCA - average precision score – 0.72

3.  Linear regression on Components obtained by Partial least square technique – 0.68

4. Bagging based approach -

Random forest on  Components obtained by partial least square technique - average precision score – 0.78
