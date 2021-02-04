R implementation of group-factor analyses in the following article:

Failure to identify robust latent variables of positive or negative valence processing across units of analysis
Yujia Peng, J.D. Knotts, Charles T. Taylor,  Michelle G. Craske, Murray B. Stein, Susan Bookheimer, Katherine S. Young, Alan N. Simmons, Hung-Wen Yeh, Julian Ruiz, Martin P. Paulus (2021) Biological Psychiatry: Cognitive Neuroscience and Neuroimaging.


##################################
### BEFORE RUNNING THE SCRIPT ###
##################################

## Getting started
Clone this repository: git clone https://github.com/jdknotts/Peng_Knotts_et_al_2021_GFA.git

### Prerequisites
* RStudio -- this script was written using RStudio Version 1.1.463. Earlier versions may have compatibility issues with some packages.

### Format input data 
The main GFA script, ‘GFA_BPCNNI.Rmd’. takes .xlsx files located in the ‘/GFA_peng_knotts_et_al/input_data/’ folder as inputs. Data should be formatted as a samples x variables matrix, with an additional first column for sample IDs and two additional header rows that should contain variable names and group assignments, respectively. Variable names and group assignments can be either numeric or strings. So the final input dataset should have a number of rows equal to the number of samples plus two, and a number of columns equal to the number of variables plus one. See example input data in the ‘/GFA_peng_knotts_et_al/input_data/’ folder for reference.

### Notes
1) Any rows that are missing data for all variables will be removed in the GFA analysis.
2) It is recommended to run the GFA script without echoing all program code in the Rstudio console by selecting Source > Source.


###########################
### RUNNING THE SCRIPT ###
###########################

### Setting local path

If using defaults, run the ‘GFA_BPCNNI.Rmd’ script and follow the requests in the Rstudio console to enter your local path to the downloaded folder. Alternatively, set the ‘setNewPath’ variable to FALSE on line 33 and enter the path to the downloaded folder on line 37.

A list of input files in the ‘/GFA_peng_knotts_et_al/input_data/’ folder will display in the Rstudio console
To select an input data file, type the index of the data file. For example, to select ‘dataSet.xlsx’, when seeing the list below you would enter 1, as follows:

1) dataSet.xlsx
2) dataSet_v2.xlsx
Enter desired file number from list above: 1

The data file ‘gfa_example_fear_data.xlsx’, included in the ‘/GFA_peng_knotts_et_al/input_data/’ folder, contains the fear conditioning data used to generate Figure 2A in Peng et al., 2021.

The script ‘rGFA_functions_BPCNNI.R’ contains supplementary functions, and is loaded automatically by ‘GFA_BPCNNI.Rmd’.

### Optional settings

To select whether or not the script saves an output file, use the ‘saveData’ variable on line 88

To select whether to use only complete cases (TRUE) or use expectation maximization imputation (FALSE), use the ‘completeOnly’ variable on line 91


###########################
### Outputs ##############
###########################

The GFA script will save the object ‘outputData’ to a file ‘/GFA_peng_knotts_et_al/output_data/gfaOutput_X.RData’, where X-1 is the number of files in the ‘/GFA_peng_knotts_et_al/output_data/’ folder prior to running the script. See lines 956-973 for descriptions of the specific variables assigned to ‘outputData’. The script also outputs several plots showing the % variance explained by resulting group factors, correlation matrices for input variables and group factors, heatmaps for group factor weight matrices, and circular plots showing median weights with standard error bars for individual group factors.
