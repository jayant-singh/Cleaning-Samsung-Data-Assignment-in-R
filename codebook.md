

  Codebook for Project
====================



       
 This codebook describes the R script, **run\_analysis.R**. This R code
comprises of following sections; \* Reading data \* Helper functions,
and \* Data manipulation.

Reading Data
------------

The data folder **"getdata-projectfiles-UCI HAR Dataset"** was unzipped
into the working directory. Using the command read.table(filename) the
relevant files were loaded into R. For example;

train\_set = read.table("X\_train.txt"), test\_set =
read.table("X\_test.txt")

Here, *train\_set* and *test\_set* refer to the training and test sets.
Similarly, other files were read. They include;

train\_id = read.table("subject\_train.txt"), test\_id =
read.table("subject\_test.txt")

activity\_train = read.table("y\_train.txt"),activity\_test =
read.table("y\_test.txt"), and

features\_text = read.table("features.txt"). All of these objects were
read as data frames.

Here:

1.  train\_id refers to subject id in the training set,
2.  test\_id refers to subject id in test set,
3.  activity\_train refers to the activitylabels in training set,
4.  activity\_test refers to activitylabels in test set,
5.  features\_text refers to entire list of features, i.e.mesurements.
    There are 561 measurements, which were taken on the subjects.

Helper Functions
----------------

To avoid repetition of code and to make the code more readable, several
auxiliary functions were implmented. They are
*function\_assign.R*,*strip.R*, and *shaping.R*. These functions have
been called in the main program, **run_analysis.R**. For more
details regarding these functions, please refer to the readme.md.

Data Manipulation
-----------------

The transformation of data consists of following steps: 1. To begin
with, train\_id is merged with train\_set.Similarly, test\_id is merged
with test\_set.

2.  Next, we merge train\_set and test\_set to form train\_test.

3.  Then, the two activities set, activity\_train and activity\_test are
    merged together to get activity\_train\_test.

4.  We call the function function\_assign () on activity\_train\_test to
    assign text labels to the activity labels(**1**,....,**6**). The
    text labels are provided in the file **activity\_labels**.

5.  After assigning text labels to the activities, we merge the
    activity\_train\_test and train\_test to get the complete data set,
    called **train\_test\_new**. It is a data frame.

6.  Next, we extract only those columns from train\_test\_new, which
    correspond to mean and standard deviation for each measurement.The
    resulting data frame is called **train\_test\_mean\_std**.

7.  Next, we call the strip() function on features\_text, so as to label
    the variables appropriately.

8.  At this step, we have a data set, which contains only variables,
    corresponding to mean and standard deviations for each measurement.
    Moreover, all the variables are named appropriately, in the new data set called **train\_test\_mean\_std\_new**.

9.  Our next job was to melt the data set,(obtained in above step).
    Using function shaping() the data set was melted and then dcasted
    into a wide format, so that the average value of each variable for
    each user ID and activity can be calculated.

10. The final tidy set with the required measurements has 180
    observations and 68 variables, and has been loaded into
    **data\_ID\_activity\_mean**. This is a data frame with 180
    observations on 68 variables. Here **"ID"** is a numeric vector,
    **"Activity"** is a character vector, and rest variables are numeric
    vectors.








