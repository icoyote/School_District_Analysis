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
 The impact would have been greater if the grades were turned to 0 instead of NaN


How is the school summary affected?

In this section is where we can fully apprecaite the impact of invalidadting that set of 9th grade scoresfor the Thomas High School

![](/Images/newPerSchoolSummary.png)

It is at this point that having changed the math and reading scores for the ninth graders that we can see a bigger impact.
the calculation of the Thomas High School’s performance is still calculated with the total of all it's students however the NaN scores drove the percentages of passing students down.

Per School Summary % | after NaN values | before NaN values
------------- | ------------- | -------------
% passing math | **66.9**  | 93.3
% passing reading  | **69.7** | 97.3
% overall passing | **65.1**| 90.6

Relative to other schools the drop of the overall passing % dropped from 90.6% to 65.1% placing the Thomas High School from the top 2 spot to the second last in the botoom ranking.
This is mainly due to still take into passing consideration all the students in the 9th grade, they do not pass the validation (because NaN is not greater than 70)

```
# Calculate the students who passed both math and reading.
per_passing_math_reading = school_data_complete_df[(school_data_complete_df["math_score"] >= 70) 
                                              & (school_data_complete_df["reading_score"] >= 70)]
```


For the remaining operations it was requested to identify the total number of students with NaN scores for the Thomas High School and re-calculate the percentage of students passing math, reading and both

![](/Images/newStudentValues.png)

461 students were counted for the 9th grade and once the calculations for the School Summary were adjusted, the Thomas High School recovered it's top2 position:

![](/Images/newUpdatedPerSchoolSummary.png)

Even without this correction the rest of the analysis sections were only affected by very small variations on their percentages, sometimes not even noticeable when the formatting was applied.

Per School Summary % | after NaN values |Updated percentages removing count for 9th graders
------------- | ------------- | -------------
% passing math | 66.9  | **93.2**
% passing reading  | 69.7 | **97.0**
% overall passing | 65.1| **90.6**


Math and reading scores by grade, Scores by school spending, Scores by school size and Scores by school type had very small variations (at the centimal level sometimes) which didn't affect these sortings



