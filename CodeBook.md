# Code Book

This document describes the code inside `run_analysis.R` by each function.

## function execution - executions all the rest of the functions
* Set the source of data zip file
* Execute all the rest of the functions
* Return output data set

## function downloadinput - download source files

* Download the `UCI HAR` zip file if it doesn't exist
* Unzip the `UCI HAR` zip file into `UCI HAR Dataset` folder

## function bindtables - read & bind data tables

* Read the test data set from `UCI HAR Dataset/test/X_test.txt` as dataTest
* Read the test activity labels from `UCI HAR Dataset/test/y_test.txt.txt` as labelTest
* Read the test subjects data from `UCI HAR Dataset/test/subject_test.txt.txt` as subjectTest
* Merge all test data sets into one (tables dataTest, labelTest and subjectTest)
* Rename Activity and Subject variables for test data set
* Read the training data set from `UCI HAR Dataset/train/X_train.txt.txt` as dataTrain
* Read the training activity labels from `UCI HAR Dataset/train/y_train.txt.txt` as labelTrain
* Read the training subjects data from `UCI HAR Dataset/train/subject_train.txt.txt` as subjectTrain
* Merge all training data sets into one (tables dataTrain, labelTrain and subjectTrain)
* Rename Activity and Subject variables for training data set
* Merge test and training data sets into one (data)

## function fixvariables - rename activity & other variable names to make them descriptive
* Read descriptive activity names from `activity_labels.txt` as labelAct
* Add activity names as factor to the data set
* Read descriptive variable names from `features.txt` as labelVar
* Rename variable names in the data set by labelVar
   
## function organiseoutput - return organised output with selected variables
* Find variables with means and standard deviation only
* Drop all other variables in the data set
* Generate output data set with the average of (i) each variable for (ii) each activity and (iii) each subject

At this point the final data set looks like:

    > head(meanAndStdAverages[, 1:5], n=3)
      Activity Subject tBodyAcc.mean...X tBodyAcc.mean...Y tBodyAcc.mean...Z
    1  WALKING       1         0.2773308       -0.01738382        -0.1111481
    2  WALKING       2         0.2764266       -0.01859492        -0.1055004
    3  WALKING       3         0.2755675       -0.01717678        -0.1126749

## function saveoutput - save output as csv file
* Write output data to `output.csv`
