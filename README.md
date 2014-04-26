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
    
  

