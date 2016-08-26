#Getting and Cleaning Data Course Project
#This part will describe the variables, the data, and any transformations or work that I have performed to clean up the data
# the site where the data was obtained: http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones
# the data for the project:  https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip


#This file describes steps to run_analysis.R script.
# 1. unzip the data from https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip
# 2. rename fold with "traintestdata" and put all files from test and train folders in the same folder, include
#activity_lables, and features in this folder
# 3. make sure the folder "traintestdata" and run_analysis.R script are both in the current working directory
# 4. use source("run_analysis.R") command in R Console (64-bit)
# 5. you will find two output files in the current working directory
	#merged_data.txt (8150 kb): it contains a data frame called cleanedData w/ 10299 by 68 dim
	#data_with_means.txt (220 kb): it contains a data frame called result w/ 180 by 68 dim
#6. use data <- read.table("data_with_means.txt") (last two lines of code) to read the file. There are 6 activities in total
#and 30 subjects in total, we have 180 rows with all combinations for each of the 66 features.

#The run_analysis.R script performs the following steps to clean the data:
# 1. Read X_train.txt, y_train.txt and subject_train.txt from the "traintestdata" folder and store them in trainData, trainLabel,
#and trainSubject variables respectively.
# 2. Read X_test.txt, y_test.txt and subject_test.txt from the "traintestdata" folder and store them in testData, testLabel, and
#testSubject variables respectively.
# 3. Concatenate testData to trainData to generate a 10299X561 data frame, joinData
# 4. Concatenate testLabel to trainLabel to generate a 10299X1 data frame, joinLabel
# 5. Concatenate testSubject to trainSubject to generate a 10299X1 data frame, joinSubject
# 6. Read the features.txt file from the "traintestdata" folder and store the data in a variable called features.
# 7. We extract the measurements on the mena and standard deviation: this results in 66 indices list
# 8. We get a subset of joinData with the 66 corresponding columns.
# 9. Clean the column names of the subset: remove th "()" and the "-" symbols in the names, and make first leatter of "mean" and "std"
#a capital letter "M" and "S" respectively.
# 10. Read the activity_lablels.txt file from "traintestdata" folder and store the data in a variable called activity
# 11. Clean the activity names in the second column of activity. First make all names to lower cases.  If the name has an underscore between
#letters, we remove the underscore and Capitalize the letter immediately after the underscore.
# 12. Transform the values of joinLabel according to the activiety data frame
# 13. Combine the joinSubject, joinLabel, and joinData by column to get a new cleaned 10299X68 data frame, cleanedData. Properly name the first
#two columns, "subject" and "activity".  The "subject" column contains integers that range from 1 to 30 inclusive; the "activity" column contains
#6 kinds of activity names; the last 66 columns contain measurements that range from -1 to 1 exclusive.
# 14. Write the cleanedData out to "Merged_data.txt" file in current working directory.
# 15. Generate a second independent tidy data set with the average of each unique activity, which result in a 180 combinations of the two. Then for
#each combination, calculate the mean of each measurement with the corresponding combination. Initialize the result data frame and performing two
#for-loops we get a 180X68 data frame
# 16. Write the result out to "data_with_means.txt" file in current working directory.
