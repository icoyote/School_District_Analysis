# School District analysis with Python #

## Overview of the school district analysis: ##

For this project we received 2 files containing high school data. The first file had a list of high schools with their budget and the second file had a listing of students belonging to the high schools and their math and reading grades.

During the review of the content of the files while applying data frame functionalities, it was found that some names in the **students_complete.csv** needed to be cleaned by removing Preffixes and some incorrect Suffixes founf within the student's names.

Also by merging both files and we will obtain a high-level snapshot of the district's key metrics:

- Total number of students
![](/Images/totalStudentCount.png)
- Total number of schools
![](/Images/totalSchoolsCount.png)
- Total budget
![](/Images/totalBudget.png)
- Average math score & Average reading score
![](/Images/averageScores.png)
- Percentage of students who passed math & Percentage of students who passed reading
![](/Images/percentagesMathReading.png)
- Overall passing percentage
![](/Images/overallPercentage.png)

Resulting Dataframe District Summary
![](/Images/districtSummary.png)


1. Top 5 and bottom 5 performing schools, based on the overall passing rate
![](/Images/TopAndBottom.png)
2. The average math score received by students in each grade level at each school
![](/Images/averageMathByGrade.png)
3. The average reading score received by students in each grade level at each school
![](/Images/averageReadByGrade.png)
4. School performance based on the budget per student
![](/Images/performanceBudget.png)
5. School performance based on the school size 
![](/Images/performanceSize.png)
6. School performance based on the type of school
![](/Images/performanceType.png)


## Results: ##

Using bulleted lists and images of DataFrames as support, address the following questions.

How is the district summary affected?

After the invalidation of all the 9th grade acores for the Thomas High School
the new district summary is:

![](/Images/newDistrictSummary.png)

the values in the district summary that were not modified by the scores invalidation were the average reading score, total budget, total students.

In the first part 461 students had both their reading and math scores set to NaN, the student_count went from **39 170** to **38 709** which is less that a 2% change in the total student number, in general the passing math percentages and passing reading percentages changed very little as well

percentages   | after NaN values | before NaN values
------------- | ------------- | -------------
passing_math_percentage  | **74.8**  | 75
passing_reading_percentage  | **85.7** | 86
overall_passing_percentage | **64.9**| 65
average math score | **78.9** | 79.0


 we do notice that by invalidating the grades for the 9th grade of Thomas High School the passing grade has a slighly lower value


How is the school summary affected?

How does replacing the ninth graders’ math and reading scores affect Thomas High School’s performance relative to the other schools?
How does replacing the ninth-grade scores affect the following:
Math and reading scores by grade
Scores by school spending
Scores by school size
Scores by school type

## Summary ##

 Summarize four changes in the updated school district analysis after reading and math scores for the ninth grade at Thomas High School have been replaced with NaNs

