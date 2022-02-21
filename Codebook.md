The run_analysis.R script performs data preparation followed by the steps based
on the course instructions provided.

1.  **Download the dataset**

    -   Dataset downloaded and extracted in the “UCI HAR Dataset” folder.

2.  **Assign each data to variables**

    -   features \<- features.txt : 561 rows, 2 columns  
        *Features selected come from the accelerometer and gyroscope 3-axial raw
        signals tAcc-XYZ and tGyro-XYZ.*

    -   activities \<- activity_labels.txt : 6 rows, 2 columns  
        *Activities performed when measurements were taken and codes (labels)*

    -   subject_test \<- test/subject_test.txt : 2947 rows, 1 column  
        *Contains test data of test subjects being observed*

    -   x_test \<- test/X_test.txt : 2947 rows, 561 columns  
        *Contains recorded features of test data*

    -   y_test \<- test/y_test.txt : 2947 rows, 1 columns  
        *Contains test data of activities code labels*

    -   subject_train \<- test/subject_train.txt : 7352 rows, 1 column  
        *Contains train data of volunteer subjects*

    -   x_train \<- test/X_train.txt : 7352 rows, 561 columns  
        *Contains recorded features train data*

    -   y_train \<- test/y_train.txt : 7352 rows, 1 columns  
        *Contains train data of activities’code labels*

3.  **Creates on dataset by merging training and test sets**

    -   X (10299 rows, 561 columns) is created by merging x_train and x_test
        using rbind() function

    -   Y (10299 rows, 1 column) is created by merging y_train and y_test using
        rbind() function

    -   Subject (10299 rows, 1 column) is created by merging subject_train and
        subject_test using rbind() function

    -   Merged_Data (10299 rows, 563 column) is created by merging Subject, Y
        and X using cbind() function

4.  **Extracts mean and standard deviation for each measurement**

    -   TidyData (10299 rows, 88 columns) is created by subsetting Merged_Data,
        selecting only columns: subject, code and the mean and *standard
        deviation* (std) for each measurement

5.  **Uses names of descriptive activity to name activities in the data set**

    -   Entire numbers in the code column of the TidyData replaced with
        corresponding activity taken from second column of the activities
        variable

6.  **Labels the data set with descriptive variable names**

    -   code column in TidyData renamed to activities

    -   All Acc in column’s name replaced by Accelerometer

    -   All Gyro in column’s name replaced by Gyroscope

    -   All BodyBody in column’s name replaced by Body

    -   All Mag in column’s name replaced by Magnitude

    -   All starting with character f in column’s name replaced by Frequency

    -   All starting with character t in column’s name replaced by Time

7.  **From the data set in step 4, creates a second, independent tidy data set
    with the average of each variable for each activity and each subject**

    -   FinalData (180 rows, 88 columns) is created by sumarizing TidyData
        taking the means of each variable for each activity and each subject,
        grouped by subject and activity.

    -   Export FinalData into FinalData.txt file.
