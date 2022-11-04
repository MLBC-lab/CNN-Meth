
# CNN-Meth

CNN-Meth is a machine learning tool for predicting if a given lysine is a methylation binding site. Protein lysine methylation is a particular type of post translational modification (PTM) that plays an important role in both histone and non-histone function regulation in proteins. Deregulation caused by lysine methyltransferases has been identified as the cause of several diseases including cancer as well as both mental and developmental disorders. Methylation is reversible and so identifying binding sites is critical to treating diseases resulting from this PTM.





## Evaluating Test Set

The independent test set used to evaluate CNN-Meth is included in this repository and was not used for training. To run CNN-Meth against the entire test set, use the command shown below.
```
python evaluate-test-set.py
```
## Usage

```
python cnn-meth.py <path to feature file>
```
## Making Feature Files

To generate a feature file for a given sequence, the PSSM and secondary structure values must be generated separately using psi-blast and SPIDER2 respectively.  CNN-Meth supports polypeptide sequences of 31 amino acids with the lysine in question at the center. The PSSM and SPIDER2 values corresponding to the target sequence must be serialized as two dimensional numpy arrays and placed into the PSSM and SPD3 folders, respectively. The file names of the PSSM and SPIDER2 subsequences must be the 31 amino acid characters followed by an extension of either .spssm or .sspd3 respectively. Two samples have been included in this repository as a reference. Once the .spssm and .sspd3 files are in place, the feature file can be generated using the following command.
```
python makefeatures.py
```

## Training Data

CNN-Meth was trained using data extracted from the Protein Lysine Modification Database (PLMD) [1-3]. This dataset contains various types of lysine PTMs that have been experimentally verified. Specifically, the methylation dataset consists of 6322 methylation sites and 133293 non-methylation sites. To reduce bias within our model, CD-HIT was used to remove sequences with greater than 40\% sequential similarity. After removing similar sequences, our dataset consisted of 4913 methylation sites and 108958 non-methylation sites.

<small>1.  Xu H, Zhou J, Lin S, Deng W, Zhang Y, Xue Y. PLMD: an updated data resource of protein lysine modifications. Journal of Genetics and Genomics. 2017;44(5):243-250. </small>

<small>2. Liu Z, Wang Y, Gao T, et al. CPLM: a database of protein lysine modifications. Nucleic acids research. 2014;42(D1):D531-D536. </small>

<small>3. Liu Z, Cao J, Gao X, et al. CPLA 1.0: an integrated database of protein lysine acetylation. Nucleic acids research. 2011;39(suppl\_1):D1029-D1034. </small>
