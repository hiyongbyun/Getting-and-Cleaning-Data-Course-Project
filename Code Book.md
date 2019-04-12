## Code Book

Following files were imported for analysis:
* features.txt: List of all features (variables).
* activity_labels.txt: Contains activity names.
* train/X_train.txt: Training set containing 7352 observations and 561 variables.
* train/y_train.txt: Training labels for 561 variables.
* train/subject_train.txt: Subject IDs for 7352 observations.
* test/X_test.txt: Test set containing 7352 observations and 561 variables.
* test/y_test.txt: Test labels for 561 variables.
* test/subject_test.txt: Subject IDs for 7352 observations.
* train/subject_train.txt: Each row identifies the subject who performed the activity, ranging between 1 and 30.


Following files were imported as data frames which were then merged:
* features.txt
* X_train.txt
* y_train.txt
* X_test.txt
* y_test.txt

86 variables containing "mean" and "std" were selected from the 561 variables. They were then renamed as per tidy data variable naming principles:
```
"timebodyaccelerationmeanx" "timebodyaccelerationmeany" "timebodyaccelerationmeanz" "timebodyaccelerationstdx" "timebodyaccelerationstdy" "timebodyaccelerationstdz" "timegravityaccelerationmeanx" "timegravityaccelerationmeany" "timegravityaccelerationmeanz" "timegravityaccelerationstdx" "timegravityaccelerationstdy" "timegravityaccelerationstdz" "timebodyaccelerationjerkmeanx" "timebodyaccelerationjerkmeany" "timebodyaccelerationjerkmeanz" "timebodyaccelerationjerkstdx" "timebodyaccelerationjerkstdy" "timebodyaccelerationjerkstdz" "timebodygyromeanx" "timebodygyromeany" "timebodygyromeanz" "timebodygyrostdx" "timebodygyrostdy" "timebodygyrostdz" "timebodygyrojerkmeanx" "timebodygyrojerkmeany" "timebodygyrojerkmeanz" "timebodygyrojerkstdx" "timebodygyrojerkstdy" "timebodygyrojerkstdz" "timebodyaccelerationmagnitudemean" "timebodyaccelerationmagnitudestd" "timegravityaccelerationmagnitudemean" "timegravityaccelerationmagnitudestd" "timebodyaccelerationjerkmagnitudemean" "timebodyaccelerationjerkmagnitudestd" "timebodygyromagnitudemean" "timebodygyromagnitudestd" "timebodygyrojerkmagnitudemean" "timebodygyrojerkmagnitudestd" "frequencybodyaccelerationmeanx" "frequencybodyaccelerationmeany" "frequencybodyaccelerationmeanz" "frequencybodyaccelerationstdx" "frequencybodyaccelerationstdy" "frequencybodyaccelerationstdz" "frequencybodyaccelerationmeanfreqx" "frequencybodyaccelerationmeanfreqy" "frequencybodyaccelerationmeanfreqz" "frequencybodyaccelerationjerkmeanx" "frequencybodyaccelerationjerkmeany" "frequencybodyaccelerationjerkmeanz" "frequencybodyaccelerationjerkstdx" "frequencybodyaccelerationjerkstdy" "frequencybodyaccelerationjerkstdz" "frequencybodyaccelerationjerkmeanfreqx" "frequencybodyaccelerationjerkmeanfreqy" "frequencybodyaccelerationjerkmeanfreqz" "frequencybodygyromeanx" "frequencybodygyromeany" "frequencybodygyromeanz" "frequencybodygyrostdx" "frequencybodygyrostdy" "frequencybodygyrostdz" "frequencybodygyromeanfreqx" "frequencybodygyromeanfreqy" "frequencybodygyromeanfreqz" "frequencybodyaccelerationmagnitudemean" "frequencybodyaccelerationmagnitudestd" "frequencybodyaccelerationmagnitudemeanfreq" "frequencybodybodyaccelerationjerkmagnitudemean" "frequencybodybodyaccelerationjerkmagnitudestd" "frequencybodybodyaccelerationjerkmagnitudemeanfreq" "frequencybodybodygyromagnitudemean" "frequencybodybodygyromagnitudestd" "frequencybodybodygyromagnitudemeanfreq" "frequencybodybodygyrojerkmagnitudemean" "frequencybodybodygyrojerkmagnitudestd" "frequencybodybodygyrojerkmagnitudemeanfreq" "angletbodyaccelerationmeangravity" "angletbodyaccelerationjerkmeangravitymean" "angletbodygyromeangravitymean" "angletbodygyrojerkmeangravitymean" "anglexgravitymean" "angleygravitymean" "anglezgravitymean"
```

Above data set was merged with "subject" and "activity" labels.

The observations with vaues ranging between 1 and 6 under the "activity" column was renamed as follows:
* 1 = walking
* 2 = walkingupstairs
* 3 = walkingdownstairs
* 4 = sitting
* 5 = standing
* 6 = laying

The data frame was rearranged by "subject", then grouped by "subject" with subgroup "activity"

Average was obtained for 86 variables by applying *summarize_all* with *mean* function.
