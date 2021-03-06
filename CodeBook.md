---
title: "CodeBook"
author: "Marcus"
date: "10/25/2020"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

### 1 Downloading data-set
Dataset downloaded and extracted under the folder called UCI HAR Dataset

### 2 Assigning data to each variable
features <- features.txt : 561 rows, 2 columns 
The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.

activities <- activity_labels.txt : 6 rows, 2 columns 
List of activities performed when the corresponding measurements were taken and its labels

subject_test <- test/subject_test.txt : 2947 rows, 1 column 
contains test data of 9/30 volunteer test subjects being observed

x_test <- test/X_test.txt : 2947 rows, 561 columns 
contains recorded features from test data

y_test <- test/y_test.txt : 2947 rows, 1 columns 
contains test data of activities 

subject_train <- test/subject_train.txt : 7352 rows, 1 column 
contains train data of 21 and 30 volunteer, respectively.

x_train <- test/X_train.txt : 7352 rows, 561 columns 
contains recorded features from train data

y_train <- test/y_train.txt : 7352 rows, 1 columns 
contains train data of activities 

### 3 Merges the training and the test sets to create one data set
X (10299 rows, 561 columns) is created by merging x_train and x_test using rbind() function

Y (10299 rows, 1 column) is created by merging y_train and y_test using rbind() function
Subject (10299 rows, 1 column) is created by merging subject_train and subject_test using rbind() function

Merged_Data (10299 rows, 563 column) is created by merging Subject, Y and X using cbind() function

### 4 Collecting only the mean and standard deviation of each variable
TidyData (10299 rows, 88 columns) is created by subsetting Merged_Data, selecting only subject, code and the measurements on the mean and standard deviation for each measurement

### 5 Uses descriptive activity names to name the activities in the data set
Entire numbers in code column of the TidyData replaced with corresponding activity taken from second column of the activities variable

### 6 Label the data set with descriptive variable names
code column in TidyData renamed into activities
All Acc in column’s name replaced by Accelerometer
All Gyro in column’s name replaced by Gyroscope
All BodyBody in column’s name replaced by Body
All Mag in column’s name replaced by Magnitude
All start with character f in column’s name replaced by Frequency
All start with character t in column’s name replaced by Time

### 7 From TidyData (step 4) create a new data set consisting of means of each variable based on acitivity and subject
FinalData (180 rows, 88 columns) is created by sumarizing TidyData taking the means of each variable for each activity and each subject, after groupped by subject and activity.
Export FinalData into FinalData.txt file.




