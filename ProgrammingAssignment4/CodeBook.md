The run_analysis.R script is for preparing the data and then performs the steps required for this project. Script can be perused with the following steps.  

**Download the dataset** 
Dataset is downloaded and unziped under the folder called "UCI HAR Dataset"

**Assign each dataset to dataframes**
*features <- features.txt : 561 rows, 2 columns*
The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.
*activities <- activity_labels.txt : 6 rows, 2 columns*
List of activities performed when the corresponding measurements were taken and its codes (labels)
*subject_test <- test/subject_test.txt : 2947 rows, 1 column*
contains test data of 9/30 volunteer test subjects being observed
*x_test <- test/X_test.txt : 2947 rows, 561 columns*
contains recorded features test data
*y_test <- test/y_test.txt : 2947 rows, 1 columns*
contains test data of activities’code labels
*subject_train <- test/subject_train.txt : 7352 rows, 1 column*
contains train data of 21/30 volunteer subjects being observed
*x_train <- test/X_train.txt : 7352 rows, 561 columns*
contains recorded features train data
*y_train <- test/y_train.txt : 7352 rows, 1 columns*
contains train data of activities, code labels

**In order to create one, tidy dataset, script merges the training and the test sets**
*X (10299 rows, 561 columns)* is created by merging x_train and x_test using rbind() function
*Y (10299 rows, 1 column)*  is created by merging y_train and y_test using rbind() function
*Subject (10299 rows, 1 column)* is created by merging subject_train and subject_test using rbind() function
*merged_Data (10299 rows, 563 column)* is created by merging Subject, Y and X using cbind() function

**Calculate mean and standart deviation for each measurement and create a resulting tidy data**
*TidyData (10299 rows, 88 columns)* is created by subsetting Merged_Data, selecting only columns: subject, code and the measurements on the mean and standard deviation (std) for each measurement

**Name the activities in the dataset logically**
All numbers from the code column of TidyData is replaced by the activity names from the second column of the activities variable

**Label the datasets appropriately with logical names**
* code column in TidyData renamed into activities
* All Acc in column’s name renamed into Accelerometer
* All Gyro in column’s name renamed into Gyroscope
* All BodyBody in column’s name renamed into Body
* All Mag in column’s name renamed into Magnitude
* All start with character f in column’s name renamed into Frequency
* All start with character t in column’s name renamed into Time

**Final dataset created by the using the resulting tidy data created above with calculations of mean and standart deviation **
*FinalData (180 rows, 88 columns)* is just a summary of TidyData. We created a FinalData.csv out of this FinalData.
