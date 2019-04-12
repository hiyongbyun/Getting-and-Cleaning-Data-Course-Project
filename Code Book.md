## Code Book

Following files were imported for analysis:
* 'features.txt': List of all features.
* 'activity_labels.txt': Links the class labels with their activity name.
* 'train/X_train.txt': Training set.
* 'train/y_train.txt': Training labels.
* 'test/X_test.txt': Test set.
* 'test/y_test.txt': Test labels.
* 'train/subject_train.txt': Each row identifies the subject who performed the activity for each window sample. Its range is from 1 to 30.

Dataset Description:
Training Dataset
The training set contains 3 main datasets:-

x_train: 7352 observations of 561 variables
y_train: 7352 observations of 1 variable
sub_train: 7352 observations of 1 variable
Test Dataset
The test set contains 3 main datasets:-

x_test: 7352 observations of 561 variables
y_test: 7352 observations of 1 variable
sub_test: 7352 observations of 1 variable
Datasets used :-
1. features
dimensions: 561 observations of 2 variables

description: The 561 features selected for this database comes from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ. These time domain signals (prefix 't' to denote time) were captured at a constant rate of 50 Hz. Then they were filtered using a median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise. Similarly, the acceleration signal was then separated into body and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ) using another low pass Butterworth filter with a corner frequency of 0.3 Hz. Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals (tBodyAccJerk-XYZ and tBodyGyroJerk-XYZ). Also the magnitude of these three-dimensional signals were calculated using the Euclidean norm (tBodyAccMag, tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag). Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ, fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. (Note the 'f' to indicate frequency domain signals). These signals were used to estimate variables of the feature vector for each pattern:
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.

* tBodyAcc-XYZ
* tGravityAcc-XYZ
* tBodyAccJerk-XYZ
* tBodyGyro-XYZ
* tBodyGyroJerk-XYZ
* tBodyAccMag
* tGravityAccMag
* tBodyAccJerkMag
* tBodyGyroMag
* tBodyGyroJerkMag
* fBodyAcc-XYZ
* fBodyAccJerk-XYZ
* fBodyGyro-XYZ
* fBodyAccMag
* fBodyAccJerkMag
* fBodyGyroMag
* fBodyGyroJerkMag

The set of variables that were estimated from these signals are: 

mean(): Mean value
std(): Standard deviation
mad(): Median absolute deviation 
max(): Largest value in array
min(): Smallest value in array
sma(): Signal magnitude area
energy(): Energy measure. Sum of the squares divided by the number of values. 
iqr(): Interquartile range 
entropy(): Signal entropy
arCoeff(): Autorregresion coefficients with Burg order equal to 4
correlation(): correlation coefficient between two signals
maxInds(): index of the frequency component with largest magnitude
meanFreq(): Weighted average of the frequency components to obtain a mean frequency
skewness(): skewness of the frequency domain signal 
kurtosis(): kurtosis of the frequency domain signal 
bandsEnergy(): Energy of a frequency interval within the 64 bins of the FFT of each window.
angle(): Angle between to vectors.

Additional vectors obtained by averaging the signals in a signal window sample. These are used on the angle() variable:

gravityMean
tBodyAccMean
tBodyAccJerkMean
tBodyGyroMean
tBodyGyroJerkMean
2. x_train and x_test
dimensions: x_train - 7352 observations of 561 variables. x_test - 2947 observations of 561 variables.
description: The x_train and x_test contains the observed estimates of the features vector for 7352 cases.
3. y_train and y_test
dimensions: y_train - 7352 observations of 1 variable. y_test - 2947 observations of 1 variables.
description: The y_train and y_test contains the activityId of the 6 types of activities performed by the 7352 observations.
4. sub_train and sub_test
dimensions: sub_train - 7352 observations of 1 variable. sub_test - 2947 observations of 1 variables.
description: The sub_train and sub_test contains the subjectId of the 30 subjects who were used to collect the 7352 observations.
5. act_label
dimensions: 6 observations of 2 variables.

description: The act_label dataset contains the labels for the 6 types of activities performed:-

WALKING
WALKING_UPSTAIRS 3.WALKING_DOWNSTAIRS
SITTING
STANDING
LAYING
Getting and Cleaning the datasets:
Merge training and test sets.
The following text files were imported:
features.txt
activity.txt
Assign appropriate column names to act_label datasets indicating activityId and activityType.

The following text files were imported:
X_train.txt

Y_train.txt

subject_train.txt

X_test.txt

Y_test.txt

subject_test.txt

Assign approproate column names to x_train and x_test which indicates the features of the dataset. Use features dataset to do the function. Assign approproate column names to y_train and y_test which indicates the activityId. Assign approproate column names to sub_train and sub_test which indicates the subId. Join the x_train, x_test and sub_train to create a training dataset and y_train, y_test and sub_tesy to create a test dataset.

Finally, merge the training and test dataset to create the merged_set.
Extracts only the measurements on the mean and standard deviation for each measurement.
A logical vector was created using grepl() to select the columns indicating mean and standard deviation and this logical vector is used to select the columns of the merged data set.

Use descriptive activity names to name activities in data set.
The activityId of the merged dataset was matched with the activity labels dataset and the values of activityId were replaced with the activtyType. ActivityId will indicate the activity names in the merged data set.

Appropriately labels the data set with descriptive variable names.
A tidy dataset was created to clean the variable names containing unwanted characters and proper variable names were assigned using gsub().

Create a second, independent tidy data set with the average of each variable for each activity and each subject.
Use the group_by() and summarize_all() to create a tidy data set containing the averagae of each variable grouped by activity and subject.

Write the final tidy dataset to tidydata.txt
Use the write.table() to write the tidy data set to tidydata.txt.
