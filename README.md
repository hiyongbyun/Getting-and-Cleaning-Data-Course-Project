# Getting and Cleaning Data Course Project

### Samsung data set downloaded from https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

### Load dplyr package
`library(dplyr)`

### Store variable names by reading features.txt
```
features <- read.table("UCI HAR Dataset/features.txt")
features <- t(features$V2)`
```

### Store subject ID by reading subject_test.txt and subject_train.txt
```
subject_test <- read.table("UCI HAR Dataset/test/subject_test.txt", col.names = "subject")
subject_train <- read.table("UCI HAR Dataset/train/subject_train.txt", col.names = "subject")
subject <- rbind(subject_test, subject_train)`
```

### Store activity labels by reading y_test.txt and y_train.txt
```
activity_test <- read.table("UCI HAR Dataset/test/y_test.txt", col.names = "activity")
activity_train <- read.table("UCI HAR Dataset/train/y_train.txt", col.names = "activity")
activity <- rbind(activity_test, activity_train)`
```

### Store feature vector by reading X_test.txt and X_train.txt
```
test_data <- read.table("UCI HAR Dataset/test/X_test.txt", col.names = features)
train_data <- read.table("UCI HAR Dataset/train/X_train.txt", col.names = features)
merged_data <- rbind(test_data, train_data)`
```

### Merge subject ID, activity labels and feature vector data
`merged_data <- cbind(subject, activity, merged_data)`

### Select variables containing subject, activity, mean, and std
`mean_std_data <- select(merged_data, subject, activity, matches("mean|std"))`

### Name activities
```
mean_std_data$activity[mean_std_data$activity == 1] <- "walking"
mean_std_data$activity[mean_std_data$activity == 2] <- "walkingupstairs"
mean_std_data$activity[mean_std_data$activity == 3] <- "walkingdownstairs"
mean_std_data$activity[mean_std_data$activity == 4] <- "sitting"
mean_std_data$activity[mean_std_data$activity == 5] <- "standing"
mean_std_data$activity[mean_std_data$activity == 6] <- "laying"
```

### Fix variable names
```
fix_variable_names <- colnames(mean_std_data)
fix_variable_names <- sub("^t", "time", fix_variable_names)
fix_variable_names <- sub("^f", "frequency", fix_variable_names)
fix_variable_names <- sub("Acc", "acceleration", fix_variable_names)
fix_variable_names <- sub("Mag", "magnitude", fix_variable_names)
fix_variable_names <- gsub("\\.", "", fix_variable_names)
fix_variable_names <- tolower(fix_variable_names)`
```

### Rename data frame columns
`names(mean_std_data) <- fix_variable_names`

### Group by subjects and activity
`subject_mean_std_data <- group_by(mean_std_data, subject, activity)`

### Arrange by subject ID
`subject_mean_std_data <- arrange(subject_mean_std_data, subject)`

### Summarize with averages for all variables
`average_data <- summarize_all(subject_mean_std_data, mean)`

### Output tidy data set containing average values
`View(average_data)`
