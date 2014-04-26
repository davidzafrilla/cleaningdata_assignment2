cleaningdata_assignment2
========================

The run_analysis.R file should be downloaded to the directory where the data are stored.

In order to make it work from R, you should type:

source(run_analysis.R)

The script works as follows:

1) It loads the files for:

    * Activity Labels
    * Features
    
2) For both, train and test datasets

  2.1) Load the subject dataset and measurements dataset
  2.2) Selects the columns with mean(),Mean() and std() to get the desired variables from the measurements dataset
  2.3) Removes the columns that should not be included in the tidydata set
  2.4) Load activity data set
  2.5) Transforms activity factor into the right text category label (and then, again convert it to a factor)
  2.6) Build a new dataset (one for each) binding columns of subject_id, activity, and measurements
  
3) Builds a dataset by binding rows from train dataset and test dataset.

4) Deletes auxiliary variables

5) Creates an empty dataframe (tidydata)

5) For each subject_id:

  5.1) Get the subset corresponding to each activity type
  5.2) Calculate the mean of the measurements for this activity type
  5.3) Store the result as a row in tidydata.
  
6) After every subject_id(30) and every activity type(6), we get a new dataset (tidydata) with 30x6=180 rows.
The columns correspond to the variables selected:
    * the ones containing "mean()"
    * the ones containing "std()"
    * the ones containing "Mean"
    
  
CodeBook
=========

subject_id: identifier of the subject who carried out the experiment

activity: activity label

Mean of the feature vector for each pattern:  
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.

tBodyAcc.mean...XYZ
tGravityAcc.mean...XYZ
tBodyAccJerk.mean...XYZ
tBodyGyro.mean...XYZ
tBodyGyroJerk.mean...XYZ
tBodyAccMag.mean
tGravityAccMag.mean
tBodyAccJerkMag.mean
tBodyGyroMag.mean
tBodyGyroJerkMag.mean
fBodyAcc.meanFreq...XYZ
fBodyAccJerk.meanFreq...XYZ
fBodyGyro.meanFreq...XYZ
fBodyAccMag.mean
fBodyAccJerkMag.mean
fBodyGyroMag.mean
fBodyGyroJerkMag.mean

Standard deviation of the feature vector for each pattern:  
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.

tBodyAcc.std...XYZ
tGravityAcc.std...XYZ
tBodyAccJerk.std...XYZ
tBodyGyro.std...XYZ
tBodyGyroJerk.std...XYZ
tBodyAccMag.std
tGravityAccMag.std
tBodyAccJerkMag.std
tBodyGyroMag.std
tBodyGyroJerkMag.std
fBodyAcc.std...XYZ
fBodyAccJerk.std...XYZ
fBodyGyro.std...XYZ
fBodyAccMag.std
fBodyAccJerkMag.std
fBodyGyroMag.std
fBodyGyroJerkMag.std

vectors obtained by averaging the signals in a signal window sample. These are used on the angle() variable:

angle.tBodyAccMean.gravity
angle.tBodyAccJerkMean..gravityMean
angle.tBodyGyroMean.gravityMean
angle.tBodyGyroJerkMean.gravityMean
angle.X.gravityMean
angle.Y.gravityMean
angle.Z.gravityMean                

