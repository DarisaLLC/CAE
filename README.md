# CAE
Canonical Autocorrelation Embeddings
## Dependencies
```
install.packages('caret')
install.packages('TunePareto')
install.packages('pROC')
install.packages('reshape')
install.packages('plyr')
install.packages('rpart')

```

Note: When installing 'caret', if there is an error caused by package 'dimRed' (which stems from an issue with package 'Biobase', run code below:
```
if (!requireNamespace("BiocManager", quietly = TRUE))
    install.packages("BiocManager")
BiocManager::install("Biobase", version = "3.8")
install.packages('dimRed')
```

## Additional dependencies for test code

```
install.packages('eegkitdata')
```

## Working directory
Note that for the relative paths to work, it is necessary for the working directory to be set to the file's directory. If you are using R Studio, note that this is often not the default option.

## CAA and CAE
CAA and CAE code are contained in the folder CAE/


## Test code
A sample code is provided to run CAE with publicly available data. This is contained on test/Notebook_CAE.Rmd. The data used tackles the task of predicting alcoholism from EEG signals. This is a small dataset (20 patients) made available by the 'eegkitdata' package, and is included here to provide a reproducible example. 

## Prediction of neurological recovery of comatose survivors of cardiac arrest:

The code provided in the folder PLOS_EEG allows you to reproduce the results of the PLOS paper 'Predicting neurological recovery with Canonical Autocorrelation Embeddings': https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0210966. 
To run this code, you will need access to the data, which will be made available by UPMC to those entering a data agreement with the institution. For more information refer to the data availability statement in the paper. 

Once you have the data, make sure to include it in the 'data' folder. The data should include:
1. PatientSummary.csv
2. Folder titled 'EEG': Within this folder, there must be one csv file per patient, the name of the file must be the patient's id.

Once the data is in place, run the script 'extract_CAA.R'. This script (i) finds the subset of patients to be included in the experiments, according to the length of stay, quality of data and survival to discharge, (ii) applies CAA to the data of each patient, (iii) stores the data in data/CAA_EEG.RData.

After storing the CAA representation of the EEG, run the script in the R Notebook Notebook_CAE.Rmd.

### Sample data
In PLOS_EEG/data/ sample data corresponding to one minute of EEG recording for two patients is provided, in order to allow researchers to gain insight into the data structure.
