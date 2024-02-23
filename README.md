# Random Forest GPU
#### Omar Halawa (ohalawa@ucsd.edu) of the GenePattern Team @ Mesirov Lab - UCSD
\
The following repository is a GenePattern module written in Python 3, using the following [Singularity container](https://github.com/genepattern/nmf-gpu/blob/master/docker/Singularity.def). 
\
It performs either <ins>cross-validation</ins> (takes one dataset as input) or <ins>test-train prediction</ins> (takes two datasets, test and train). Each dataset consists of two file inputs, one for feature data (.gct), and one for target data (.cls). It processes files and performs [random forest classification](/docs/randomforest.md), an _ensemble_ machine learning algorithm, on them using RAPIDS.ai's RandomForestClassifier, generating a prediction results file (.pred.odf) that compares the "true" class to the model's prediction and outputting a feature importance file (.feat.odf) in the case of test-train prediction with a training dataset. The module also supports importing and exporting trained models. Created for GenePattern module usage through optional arguments for classifier parameters.

Documentation on usage and implementation is found [here](/docs/tutorial.md).
A detailed step-by-step explanation behind how the Random Forest algorithm works is found [here](/docs/randomforest.md).
All source files, including cross-validation runs for all_aml_train ([.gct](/data/all_aml_train.gct), [.cls](/data/all_aml_train.cls)), BRCA_HUGO ([.gct](/data/all_aml_train.gct), [.cls](/data/all_aml_train.cls)), and iris ([.gct](/data/iris.gct), [.cls](/data/iris.cls)) datasets as well as a test-train run with all_aml_test ([.gct](/data/all_aml_test.gct), [.cls](/data/all_aml_test.cls)) and all_aml_train ([.gct](/data/all_aml_train.gct), [.cls](/data/all_aml_train.cls)) all with [output examples](/data/example_output) ("examples," as the classifier utilizes randomness, so each run varies) are available for better reproducibility and portability. However, to see how randomness could potentially be "reproduced," read [this](/data/example_output/reproduc.md).

This module is a GPU-backed implementation which may be faster compared to the original [RandomForest](https://github.com/genepattern/RandomForest) module.
