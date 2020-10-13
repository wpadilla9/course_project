run_analysis.R script performs data preparation and then follows by the 5 steps required with this project.
1. Download the dataset
  - Download dataset and extracted under the folder called UCI HAR Dataset.
2. Assign each data to variables
  - features<-features.txt: 561 obs. of 2 variables (features selected from accelerometer and gyroscope)
  - activites<-activity_labels.txt: 6 obs. of 2 variables (list of activities when measurements taken)
  - subject_test<-test/subject_test.txt: 2947 obs. of 1 variable (contains test data of 9/30 volunteer test subjects being observed)
  - x_test<-test/X_test.txt: 2947 obs. of 1 variable (contains features of test data)
  - y_test<-test/y_test.txt: 2947 obs. of 1 variable (contains test data of activities' code labels)
  - subject_train<-test/subject_train.txt: 7352 obs. of 1 variable (contains train data of 21/30 volunteer subjects being observed)
  - x_train<-test/X_train.txt: 7352 obs. of 1 variable (contains recorded features train data)
  - y_train<-test/y_train.txt: 7352 obs. of 1 variable (contains train data of activities' code labels)
3. Merge training and test sets to create one data set
  - x (10299 obs of 561 variables) created by merging x_train and x_test using rbind() function
  - y (10299 obs of 561 variables) created by merging y_train and y_test using rbind() function
  - Subject (10299 obs of 561 variables) created by merging subject_train and subject_test using rbind() function
  - Merged_Data (10299 obs of 561 variables) created by merging Subject, Y and X using cbind()
4. Extracts measurements on the mean and standard deviation for each measurement
  - TidyData (10299 obs of 88 variables) is created by subsetting Merged_Data, selecting columns subject, code and the measurements on the mean and std deviation for each measurement
5. Uses descriptive activity names to name the activities in the data set
  - Numbers in code column of TidyData replaced with corresponding activity taken from the second column of activities variable
6. Label data set with descriptive variable names
  - Code column in TidyData renamed activities
  - All Acc in column's name replaced by Accelerometer
  - All Gyro in column's name replaced by Gyroscope
  - All BodyBody in column's name replaced by Magnitude
  - All Mag in column's name replaced by Magnitude
  - All start with character f in column's name replaced by Frequency
  - All start with character t in column's name replaced by Time
7. From data in step 4, create a second, independent tidy data set with the average of each variable for each activity and each subject
  - FinalData (180 obs for 88 variables) created by summarizing TidyData taking the means of each variable for each activity and each subject 
  - Export FinalData into FinalData.txt file
