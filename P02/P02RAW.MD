Expected Date of Completion:..................................... Actual Date of Completion:.......................
----------------------------------------------------------------------------------------------------------------
Group A
Assignment No: 2
----------------------------------------------------------------------------------------------------------------
Title of the Assignment: Data Wrangling, II
Create an “Academic performance” dataset of students and perform the following
operations using Python.
1. Scan all variables for missing values and inconsistencies. If there are missing
values and/or inconsistencies, use any of the suitable techniques to deal with
them.
2. Scan all numeric variables for outliers. If there are outliers, use any of the suitable
techniques to deal with them.
3. Apply data transformations on at least one of the variables. The purpose of this
transformation should be one of the following reasons: to change the scale for
better understanding of the variable, to convert a non-linear relation into a linear
one, or to decrease the skewness and convert the distribution into a normal
distribution.
Reason and document your approach properly.
----------------------------------------------------------------------------------------------------------------
Objective of the Assignment: Students should be able to perform thedata wrangling
operation using Python on any open source dataset
Department of Computer Engineering Subject : DSBDAL
Prerequisite:
1. Basic of Python Programming
2. Concept of Data Preprocessing, Data Formatting , Data Normalization and Data
Cleaning.
---------------------------------------------------------------------------------------------------------------
Contents for Theory:
1. Creation of Dataset using Microsoft Excel.
2. Identification and Handling of Null Values
3. Identification and Handling of Outliers
4. Data Transformation for the purpose of :
a. To change the scale for better understanding
b. To decrease the skewness and convert distribution into normal distribution
---------------------------------------------------------------------------------------------------------------
Theory:
1. Creation of Dataset using Microsoft Excel.
The dataset is created in “CSV” format.
● The name of dataset is StudentsPerformance
● The features of the dataset are: Math_Score, Reading_Score, Writing_Score,
Placement_Score, Club_Join_Date .
● Number of Instances: 30
● The response variable is: Placement_Offer_Count .
● Range of Values:
Math_Score [60-80], Reading_Score[75-,95], ,Writing_Score [60,80],
Placement_Score[75-100], Club_Join_Date [2018-2021].
● The response variable is the number of placement offers facilitated to particular
students, which is largely depend on Placement_Score
To fill the values in the dataset the RANDBETWEEN is used. Returns a random
integer number between the numbers you specify
Syntax : RANDBETWEEN(bottom, top) Bottom The smallest integer and
Top The largest integer RANDBETWEEN will return.
Step 4: In 20% data, fill the impurities. The range of math score is [60,80], updating a
few instances values below 60 or above 80. Repeat this for Writing_Score [60,80],
Placement_Score[75-100], Club_Join_Date [2018-2021].
Step 5: To violate the ruleof response variable, update few valus . If placement scoreis
greater then 85, facilated only 1 offer.
The dataset is created with the given description.
2. Identification and Handling of Null Values
Missing Data can occur when no information is provided for one or more items or for a
whole unit. Missing Data is a very big problem in real-life scenarios. Missing Data can
also refer to as NA(Not Available) values in pandas. In DataFrame sometimes many
datasets simply arrive with missing data, either because it exists and was not collected or
it never existed. For Example, Suppose different users being surveyed may choose not to
share their income, some users may choose not to share the address in this way many
datasets went missing.
In Pandas missing data is represented by two value:
1. None: None is a Python singleton object that is often used for missing data in
Python code.
2. NaN : NaN (an acronym for Not a Number), is a special floating-point value
recognized by all systems that use the standard IEEE floating-point
Department of Computer Engineering Subject : DSBDAL
Pandas treat None and NaN as essentially interchangeable for indicating missing
or null values. To facilitate this convention, there are several useful functions for
detecting, removing, and replacing null values in Pandas DataFrame :
●
●
●
●
●
isnull()
notnull()
dropna()
fillna()
replace()
1. Checking for missing values using isnull() and notnull()
● Checking for missing values using isnull()
In order to check null values in Pandas DataFrame, isnull() function is used. This
function return dataframe of Boolean values which are True for NaN values.
Algorithm:
Step 1 : Import pandas and numpy in order to check missing values in Pandas
DataFrame
import pandas as pd
import numpy as np
Step 2: Load the dataset in dataframe object df
df=pd.read_csv("/content/StudentsPerformanceTest1.csv")
Step 3: Display the data frame
Step 4: Use isnull() function to check null values in the dataset.
df.isnull()
Step 5: To create a series true for NaN values for specific columns. for example
math score in dataset and display data with only math score as NaN
series = pd.isnull(df["math score"])
df[series]
● Checking for missing values using notnull()
In order to check null values in Pandas Dataframe, notnull() function is used. This
function return dataframe of Boolean values which are False for NaN values.
Algorithm:
Step 1 : Import pandas and numpy in order to check missing values in Pandas
DataFrame
import pandas as pd
import numpy as np
Step 2: Load the dataset in dataframe object df
df=pd.read_csv("/content/StudentsPerformanceTest1.csv")
Step 3: Display the data frame
Department of Computer Engineering Subject : DSBDAL
See that there are also categorical values in the dataset, for this, you need to use
Label Encoding or One Hot Encoding.
from sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
df['gender'] = le.fit_transform(df['gender'])
newdf=df
df
2. Filling missing values using dropna(), fillna(), replace()
In order to fill null values in a datasets, fillna(), replace() functions are used.
These functions replace NaN values with some value of their own. All these
functions help in filling null values in datasets of a DataFrame.
● For replacing null values with NaN
missing_values = ["Na", "na"]
MMIT, Lohgaon, Pune
Department of Computer Engineering Subject : DSBDAL
df = pd.read_csv("StudentsPerformanceTest1.csv", na_values =
missing_values)
df
● Filling null values with a single value
Step 1 : Import pandas and numpy in order to check missing values in Pandas
DataFrame
import pandas as pd
import numpy as np
Step 2: Load the dataset in dataframe object df
df=pd.read_csv("/content/StudentsPerformanceTest1.csv")
Step 3: Display the data frame
df
Step 4: filling missing value using fillna()
ndf=df
ndf.fillna(0)
MMIT, Lohgaon, Pune
Department of Computer Engineering Subject : DSBDAL
Step 5: filling missing values using mean, median and standard deviation of that
column.
data['math score'] = data['math score'].fillna(data['math score'].mean())
data[''math score''] = data[''math score''].fillna(data[''math
score''].median())
data['math score''] = data[''math score''].fillna(data[''math score''].std())
replacing missing values in forenoon column with minimum/maximum number
of that column
data[''math score''] = data[''math score''].fillna(data[''math score''].min())
data[''math score''] = data[''math score''].fillna(data[''math score''].max())
● Filling null values in dataset
To fill null values in dataset use inplace=true
m_v=df['math score'].mean()
df['math score'].fillna(value=m_v, inplace=True)
Filling a null values using replace() method
Following line will replace Nan value in dataframe with value -99
ndf.replace(to_replace = np.nan, value = -99)
MMIT, Lohgaon, Pune
Department of Computer Engineering Subject : DSBDAL
● Deleting null values using dropna() method
In order to drop null values from a dataframe, dropna() function is used. This
function drops Rows/Columns of datasets with Null values in different ways.
1. Dropping rows with at least 1 null value
2. Dropping rows if all values in that row are missing
3. Dropping columns with at least 1 null value.
4. Dropping Rows with at least 1 null value in CSV file
Algorithm:
Step 1 : Import pandas and numpy in order to check missing values in Pandas
DataFrame
import pandas as pd
import numpy as np
Step 2: Load the dataset in dataframe object df
df=pd.read_csv("/content/StudentsPerformanceTest1.csv")
Step 3: Display the data frame
df
Step 4:To drop rows with at least 1 null value
ndf.dropna()
MMIT, Lohgaon, Pune
Department of Computer Engineering Subject : DSBDAL
Step 5: To Drop rows if all values in that row are missing
ndf.dropna(how = 'all')
Step 6: To Drop columns with at least 1 null value.
ndf.dropna(axis = 1)
Step 7 : To drop rows with at least 1 null value in CSV file.
making new data frame with dropped NA values
new_data = ndf.dropna(axis = 

3. Identification and Handling of Outliers
3.1 Identification of Outliers
One of the most important steps as part of data preprocessing is detecting and treating the
outliers as they can negatively affect the statistical analysis and the training process of a
machine learning algorithm resulting in lower accuracy.
1. What are Outliers?
We all have heard of the idiom ‘odd one out' which means something unusual in
comparison to the others in a group.
Similarly, an Outlier is an observation in a given dataset that lies far from the rest
of the observations. That means an outlier is vastly larger or smaller than the remaining
values in the set.
2. Why do they occur?
An outlier may occur due to the variability in the data, or due to experimental
error/human error.
They may indicate an experimental error or heavy skewness in the
data(heavy-tailed distribution).
3. What do they affect?
In statistics, we have three measures of central tendency namely Mean, Median,
and Mode. They help us describe the data.
Mean is the accurate measure to describe the data when we do not have any
outliers present. Median is used if there is an outlier in the dataset. Mode is used if there
is an outlier AND about ½ or more of the data is the same.
‘Mean’ is the only measure of central tendency that is affected by the outliers
which in turn impacts Standard deviation.
MMIT, Lohgaon, Pune
Department of Computer Engineering Subject : DSBDAL
Example:
Consider a small dataset, sample= [15, 101, 18, 7, 13, 16, 11, 21, 5, 15, 10, 9]. By
looking at it, one can quickly say ‘101’ is an outlier that is much larger than the other
values.
fig. Computation with and without outlier
From the above calculations, we can clearly say the Mean is more affected than the
Median.
4. Detecting Outliers
If our dataset is small, we can detect the outlier by just looking at the dataset. But
what if we have a huge dataset, how do we identify the outliers then? We need to use
visualization and mathematical techniques.
Below are some of the techniques of detecting outliers
● Boxplots
● Scatterplots
● Z-score
● Inter Quantile Range(IQR)
4.1 Detecting outliers using Boxplot:
It captures the summary of the data effectively and efficiently with only a simple
box and whiskers. Boxplot summarizes sample data using 25th, 50th, and 75th
percentiles. One can just get insights(quartiles, median, and outliers) into the dataset by
just looking at its boxplot.
Algorithm:
Step 1 : Import pandas
Department of Computer Engineering
import numpy as np
Subject : DSBDAL
Step 2: Load the dataset in dataframe object df
df=pd.read_csv("/content/demo.csv")
Step 3: Display the data frame
df
Step 4:Select the columns for boxplot and draw the boxplot.
col = ['math score', 'reading score' , 'writing
score','placement score']
df.boxplot(col)
Step 5: We can now print the outliers for each column with reference to the box plot.
print(np.where(df['math score']>90))
MMIT, Lohgaon, Pune
Department of Computer Engineering
print(np.where(df['reading score']<25))
Subject : DSBDAL
print(np.where(df['writing score']<30))
4.2 Detecting outliers using Scatterplot:
It is used when you have paired numerical data, or when your dependent variable
has multiple values for each reading independent variable, or when trying to determine
the relationship between the two variables. In the process of utilizing the scatter plot, one
can also use it for outlier detection.
To plot the scatter plot one requires two variables that are somehow related to
each other. So here Placement score and Placement count features are used.
Algorithm:
Step 1 : Import pandas , numpy and matplotlib libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
Step 2: Load the dataset in dataframe object df
df=pd.read_csv("/content/demo.csv")
Step 3: Display the data frame
df
Step 4: Draw the scatter plot with placement score and placement offer count
fig, ax = plt.subplots(figsize = (18,10))
ax.scatter(df['placement score'], df['placement offer
count'])
plt.show()
Labels to the axis can be assigned (Optional)
ax.set_xlabel('(Proportion non-retail business
acres)/(town)')
ax.set_ylabel('(Full-value property-tax rate)/(
$10,000)')


Step 5: We can now print the outliers with reference to scatter plot.
print(np.where((df['placement score']<50) & (df['placement
offer count']>1)))
print(np.where((df['placement score']>85) & (df['placement
offer count']<3)))
4.3 Detecting outliers using Z-Score:
Z-Score is also called a standard score. This value/score helps to
understand how far is the data point from the mean. And after setting up a
threshold value one can utilize z score values of data points to define the outliers.
Zscore = (data_point -mean) / std. deviation
Algorithm:
Step 1 : Import numpy and stats from scipy libraries
import numpy as np
from scipy import stats
Step 2: Calculate Z-Score for mathscore column
z = np.abs(stats.zscore(df['math score']))
Step 3: Print Z-Score Value. It prints the z-score values of each data item
of the column
print(z)
MMIT, Lohgaon, Pune
Department of Computer Engineering Subject : DSBDAL
Step 4: Now to define an outlier threshold value is chosen.
threshold = 0.18
Step 5: Display the sample outliers
sample_outliers = np.where(z <threshold)
sample_outliers
4.4 Detecting outliers using Inter Quantile Range(IQR):
IQR (Inter Quartile Range) Inter Quartile Range approach to finding the
outliers is the most commonly used and most trusted approach used in the
research field.
IQR = Quartile3 – Quartile1
To define the outlier base value is defined above and below datasets
normal range namely Upper and Lower bounds, define the upper and the lower
bound (1.5*IQR value is considered) :
upper = Q3 +1.5*IQR
lower = Q1 – 1.5*IQR
In the above formula as according to statistics, the 0.5 scale-up of IQR
(new_IQR = IQR + 0.5*IQR) is taken.
Algorithm:
Step 1 : Import numpy library
import numpy as np
Step 2: Sort Reading Score feature and store it into sorted_rscore.
sorted_rscore= sorted(df['reading score'])
Step 3: Print sorted_rscore
sorted_rscore
Step 4: Calculate and print Quartile 1 and Quartile 3
MMIT, Lohgaon, Pune
Department of Computer Engineering Subject : DSBDAL
q1 = np.percentile(sorted_rscore, 25)
q3 = np.percentile(sorted_rscore, 75)
print(q1,q3)
Step 5: Calculate value of IQR (Inter Quartile Range)
IQR = q3-q1
Step 6: Calculate and print Upper and Lower Bound to define the
outlier base value.
lwr_bound = q1-(1.5*IQR)
upr_bound = q3+(1.5*IQR)
print(lwr_bound, upr_bound)
Step 7: Print Outliers
r_outliers = []
for i in sorted_rscore:
if (i<lwr_bound or i>upr_bound):
r_outliers.append(i)
print(r_outliers)
3.2 Handling of Outliers:
For removing the outlier, one must follow the same process of removing an entry
from the dataset using its exact position in the dataset because in all the above methods of
detecting the outliers end result is the list of all those data items that satisfy the outlier
definition according to the method used.
Below are some of the methods of treating the outliers
● Trimming/removing the outlier
● Quantile based flooring and capping
● Mean/Median imputation
MMIT, Lohgaon, Pune
Department of Computer Engineering Subject : DSBDAL
● Trimming/removing the outlier:
In this technique, we remove the outliers from the dataset. Although it is not a
good practice to follow.
new_df=df
for i in sample_outliers:
new_df.drop(i,inplace=True)
new_df
Here Sample_outliers are
12 ,16 and 17 are deleted.
So instances with index 0,
● Quantile based flooring and capping:
In this technique, the outlier is capped at a certain value above the 90th percentile value
or floored at a factor below the 10th percentile value
df=pd.read_csv("/demo.csv")
df_stud=df
ninetieth_percentile = np.percentile(df_stud['math score'], 90)
MMIT, Lohgaon, Pune
Department of Computer Engineering Subject : DSBDAL
b = np.where(df_stud['math score']>ninetieth_percentile,
ninetieth_percentile, df_stud['math score'])
print("New array:",b)
df_stud.insert(1,"m score",b,True)
df_stud
● Mean/Median imputation:
As the mean value is highly influenced by the outliers, it is advised to replace the
outliers with the median value.
1. Plot the box plot for reading score
col = ['reading score']
df.boxplot(col)
2. Outliers are seen in box plot.
3. Calculate the median of reading score by using sorted_rscore
MMIT, Lohgaon, Pune
Department of Computer Engineering Subject : DSBDAL
median=np.median(sorted_rscore)
median
4. Replace the upper bound outliers using median value
refined_df=df
refined_df['reading score'] = np.where(refined_df['reading
score'] >upr_bound, median,refined_df['reading score'])
5. Display redefined_df
6. Replace the lower bound outliers using median value
refined_df['reading score'] = np.where(refined_df['reading
score'] <lwr_bound, median,refined_df['reading score'])
7. Display redefined_df
MMIT, Lohgaon, Pune
Department of Computer Engineering Subject : DSBDAL
8. Draw the box plot for redefined_df
col = ['reading score']
refined_df.boxplot(col)
4. Data Transformation for the purpose of :
Data transformation is the process of converting raw data into a format or structure that
would be more suitable for model building and also data discovery in general.The process
of data transformation can also be referred to as extract/transform/load (ETL). The
extraction phase involves identifying and pulling data from the various source systems
that create data and then moving the data to a single repository. Next, the raw data is
cleansed, if needed. It's then transformed into a target format that can be fed into
operational systems or into a data warehouse, a date lake or another repository for use in
business intelligence and analytics applications. The transformation The data are
transformed in ways that are ideal for mining the data. The data transformation involves
steps that are.
MMIT, Lohgaon, Pune
Department of Computer Engineering Subject : DSBDAL
● Smoothing: It is a process that is used to remove noise from the dataset using some
algorithms It allows for highlighting important features present in the dataset. It
helps in predicting the patterns
● Aggregation: Data collection or aggregation is the method of storing and presenting
data in a summary format. The data may be obtained from multiple data sources to
integrate these data sources into a data analysis description. This is a crucial step
since the accuracy of data analysis insights is highly dependent on the quantity and
quality of the data used.
● Generalization:It converts low-level data attributes to high-level data attributes
using concept hierarchy. For Example Age initially in Numerical form (22, 25) is
converted into categorical value (young, old).
● Normalization: Data normalization involves converting all data variables into a
given range. Some of the techniques that are used for accomplishing normalization
are:
○ Min–max normalization: This transforms the original data linearly.
○ Z-score normalization: In z-score normalization (or zero-mean normalization)
the values of an attribute (A), are normalized based on the mean of A and its
standard deviation.
○ Normalization by decimal scaling: It normalizes the values of an attribute by
changing the position of their decimal points
● Attribute or feature construction.
○ New attributes constructed from the given ones: Where new attributes are
created & applied to assist the mining process from the given set of attributes.
This simplifies the original data & makes the mining more efficient.
In this assignment , The purpose of this transformation should be one of the
following reasons:
a. To change the scale for better understanding (Attribute or feature
construction)
Here the Club_Join_Date is transferred to Duration.
Algorithm:
Step 1 : Import pandas and numpy libraries
MMIT, Lohgaon, Pune
Department of Computer Engineering
import pandas as pd
Subject : DSBDAL
import numpy as np
Step 2: Load the dataset in dataframe object df
df=pd.read_csv("/content/demo.csv")
Step 3: Display the data frame
df
Step 3: Change the scale of Joining year to duration.
b. To decrease the skewness and convert distribution into normal distribution
(Normalization by decimal scaling)
Data Skewness: It is asymmetry in a statistical distribution, in which the curve
appears distorted or skewed either to the left or to the right. Skewness can be
quantified to define the extent to which a distribution differs from a normal
distribution.
Normal Distribution: In a normal distribution, the graph appears as a classical,
symmetrical “bell-shaped curve.” The mean, or average, and the mode, or
maximum point on the curve, are equal.
Department of Computer Engineering Subject : DSBDAL
Positively Skewed Distribution
A positively skewed distribution means that the extreme data results are larger.
This skews the data in that it brings the mean (average) up. The mean will be
larger than the median in a Positively skewed distribution.
A negatively skewed distribution means the opposite: that the extreme data
results are smaller. This means that the mean is brought down, and the median is
larger than the mean in a negatively skewed distribution.
Reducing skewness A data transformation may be used to reduce skewness. A
distribution that is symmetric or nearly so is often easier to handle and interpret
than a skewed distribution. The logarithm, x to log base 10 of x, or x to log base e
of x (ln x), or x to log base 2 of x, is a strong transformation with a major effect
on distribution shape. It is commonly used for reducing right skewness and is
often appropriate for measured variables. It can not be applied to zero or negative
values.
MMIT, Lohgaon, Pune
Department of Computer Engineering Subject : DSBDAL
Algorithm:
Step 1 : Detecting outliers using Z-Score for the Math_score variable and
remove the outliers.
Step 2: Observe the histogram for math_score variable.
import matplotlib.pyplot as plt
new_df['math score'].plot(kind = 'hist')
Step 3: Convert the variables to logarithm at the scale 10.
df['log_math'] = np.log10(df['math score'])
Step 4: Observe the histogram for math_score variable.
df['log_math'].plot(kind = 'hist')
It is observed that skewness is reduced at some level.
Conclusion: In this way we have explored the functions of the python library for Data
Identifying and handling the outliers. Data Transformations Techniques are explored with the
purpose of creating the new variable and reducing the skewness from datasets.
Assignment Question:
1. Explain the methods to detect the outlier.
2. Explain data transformation methods
3. Write the algorithm to display the statistics of Null values present in the dataset.
4. Write an algorithm to replace the outlier value with the mean of the variable.