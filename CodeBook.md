
# Variables and Data

### Step 1

`X_train`, `y_train`, `subject_train`, `X_test`, `y_test`, `subject_test` contains the data loaded from downloaded txt files. 

Then `train_test` containg the training and testing data are generated using cbind() and rbind()

### Step 2

`features` load the features corresponding to the columns of `X_train` and `X_test` files. 

`mean_and_std_positions` use grep to locate the feature names with either `mean()` or `std()`

`train_test_selected` contains the subset of `train_test` that needs further analysis.

### Step 3
`activity_labels` loads the activity labels and the corresponding activity names. It's merged with `train_test_selected` by the activity lable to get `all_data`.

`all_data` has both the activity labels and the activity names.

### Step 4

Modify `names(all_data)` to label the data set with descriptive variable names.

### Step 5
I create `tidy_data` by using aggregate() function and then save it into **tidy_data.txt** file


# tidy_data.txt

The file is the tidy data requred for submission. It's generated by the last step of the run_analysis.R code. 

The requirement says that we need to get the mean of each measurement (mean() or std() in original downloaded data) for each subject of each activity. Since all the 30 subjects performed all 6 activities, we should have 30 * 6 = 180 observations corresponding to 180 rows in the tidy data. Adding the header of the column names, we would have 181 rows in the tidy_data.txt file.

For the columns, we have 33 mean() and 33 std() measurments to average. We have 66 columns corresponding to the mean of the measurements. Adding the columns for subject number and for the activity name, we have 68 columns in total. 

This tidy data can be loaded and viewed:

```
read_tidy_data<- read.table("tidy_data.txt", header = TRUE)
View(read_tidy_data)
```

Meaning of the variables

* -mean(): Mean value
* -std(): Standard deviation
* '-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.
* prefix 't' means time domain signals
* prefix 'f' means frequency domain signals

**Unit of the variables**: unitless since all variables are normalized between -1 and 1. 

|         Variable |                                                                                   Remark                                                                                   |
|-----------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| subject_number   |                                                               The id for subjects, integers between 1 and 30                                                               |
| activity_name    | One of six activity names: WALKING, WALKING\_UPSTAIRS, WALKING\_DOWNSTAIRS,  SITTING, STANDING,LAYING |
| tBodyAcc         | Time domain body accelator signal                                                                                                                                                                           |
| tGravityAcc      | Time domain gravity accelator signal                                                                                                                                                                           |
| tBodyAccJerk     | Time domain jerk signal derived from body accelator                                                                                                                                                                           |
| tBodyGyro        | Time domain body gyroscope signal                                                                                                                                                                            |
| tBodyGyroJerk    | Time domain jerk signal derived from body gyroscop                                                                                                                                                                            |
| tBodyAccMag      | Time domain body accelator signal magnitude                                                                                                                                                                                                                                                                                                                                                    |
| tGravityAccMag   | Time domain gravity accelator signal magnitude                                                                                                                                                                           |
| tBodyAccJerkMag  | Time domain jerk signal magnitude derived from body accelator                                                                                                                                                                           |
| tBodyGyroMag     | Time domain body gyroscope signal magnitude                                                                                                                                                                           |
| tBodyGyroJerkMag | Time domain jerk signal magnitude derived from body gyroscop                                                                                                                                                                           |
| fBodyAcc         | Frequency domain body accelator signal                                                                                                                                                                           |
| fBodyAccJerk     | Frequency domain jerk signal derived from body accelator                                                                                                                                                                                                                                                              |
| fBodyGyro        | Frequency domain body gyroscope signal                                                                                                                                                                           |
| fBodyAccMag      | Frequency domain body accelator signal magnitude                                                                                                                                                                           |
| fBodyBodyAccJerkMag | Frequency domain jerk signal magnitude derived from body accelator                                                                                                                                                                           |
| fBodyBodyGyroMag         | Frequency domain body gyroscope signal magnitude                                                                                                                                                                           |
| fBodyBodyGyroJerkMag     | Frequency domain jerk signal magnitude derived from body gyroscope                                                                                                                                                                           |

Note that all variables are averaged for each activity and each subject.