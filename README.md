# School District Analysis

## Overview of the school district analysis: Explain the purpose of this analysis.

The purpose of this analysis was to measure the performance of 15 high schools across a variety of metrics (math scores, reading scores, percentage of students passing math, reading, and overall performance). To understand the factors that may contribute to the results of those metrics, we looked at the influence of variables like spending per student, the type of school (whether it was a district school or charter), and performance by grade level, among others.  

Additionally, there were concerns of systematic academic dishonesty among the 9th graders at Thomas High School (THS), which called into question the validity of all scores belonging to freshmen at THS. Since the irregularities in question are assumed to be isolated to just the 9th graders at Thomas High School , it was decided that those scores would be replaced with what are called "NaNs" (stands for Not a Number) which allow us to analyze the rest of the dataset without factoring in those possibly corrupted scores.  

Since we have both the original dataset that has the analysis including the 9th grade THS scores, as well as the modified analysis *without* them, we can easily compare both datasets to investigate the affect that the questionable scores had on the whole of the student's scores.

# Results Section

## How is the district summary affected?
- The district summary isn't that different.  When you order the schools by performance on the metric of passing **both math and reading** (which is the "% Overall Passing" column) Thomas High School is still the second highest performing school behind only Cabrera High School.  The original DataFrame had THS students passing both math and reading at 90.9480%, and the cleaned version (meaning excluding the scores of the 9th graders) had the schools students passing both at 90.6303%.  Meaning that there is actually a *very* slight increase in the overall passing percentage when you exclude the scores of 9th graders, however, that difference does not change the ranking of the school vis-a-vis it's peers in the DataFrame.

The two images below are the printouts of the district summary DataFrame. The **first image is the cleaned version**, meaning that the scores for the 9th graders at THS have been removed, leaving only the values of the schools 10th-12th graders in place to calculate the various metrics.  The **second image is the original version** meaning that scores from the 9th graders at THS **are** included.

![Alt_text](https://github.com/Nickguild1993/School_District_Analysis/blob/master/Cleaned_School_DataFrame.png)
Above is the cleaned dataframe from the (cleaned) district analysis.

![Alt_text](https://github.com/Nickguild1993/School_District_Analysis/blob/master/Original_School_DataFrame.png)
Above is the original dataframe from the district analysis.

## How is the school summary affected?
- The main way the school summary is affected is from the reduced student count at THS.  So instead of having the denominator for THS student population being 1,635 (which represents the amount of students at THS in 9th-12th grade) for the purpose of calcuating testing scores, the new denominator is 1,174- the population of 10th-12th graders at THS.  That way, you're only calculating the scores for the students not accused of scandalous academic dishonesty.  

## How does replacing the ninth graders’ math and reading scores affect Thomas High School’s performance relative to the other schools?
- The difference in how Thomas High School performs relative to other schools when you replace the 9th grader's scores is minimal.  The scores of the 10th-12th graders at THS are very consistent across grade level, so not having the 9th grade scores doesn't make much of an impact in the overall performance of THS- it is still a very high performing school, especially when compared to non-charter schools.

# How does replacing the ninth-grade scores affect the following:

## Math and reading scores by grade 
- We've attached two visuals from the analysis to show the results of replacing the 9th grade scores at THS with NaN values. The first one is a DataFrame of the reading scores by grade level across all schools, and the second image is a DataFrame of the math scores version.

![Alt_text](https://github.com/Nickguild1993/School_District_Analysis/blob/master/Cleaned_THS_reading_by_grade_DF.png)

![Alt_text](https://github.com/Nickguild1993/School_District_Analysis/blob/master/cleaned_THS_math_by_grade_DF.png)

Besides NaN values in the place of the 9th grade scores, the 10th-12th grade scores are consistent within THS and are in line with the citie's other charter schools, which perform at a much higher level across the board than the district schools.

## Scores by school spending
Below is a DataFrame of the scores of all 15 schools in bins that sort scores by how much they spend per student.

![Alt_text](https://github.com/Nickguild1993/School_District_Analysis/blob/master/Cleaned_spending_bins_DF.png)

- Thomas High School still spends between $630-$644 per student (because we're not removing the 9th graders from the school population, just their scores from the analysis. If we were to remove the entire 9th grade from the school population, then the school's total budget would be lower because they'd have 461 less students enrolled).  Which is within the 75% percentile of spending per student.  The main takeway from this above image is that Thomas High School students comfortably perform above the mean scores in all metrics in both the original and cleaned datasets.  

## Scores by school size
Below is a DataFrame of the scores sorted by school size in (3) bins, (which are the index of the DataFrame) across the different score metrics.

![Alt_text](https://github.com/Nickguild1993/School_District_Analysis/blob/master/Cleaned_scores_by_size.png)

Thomas High School, with 1635 total students and 1174 of those in 10th-12th grade, is in the second bin, which is comprised of schools with populations between 1000-2000 students.  Sorting by school size shows more about the type of school (district and charter) relative to performance.  Meaning that the charter schools have less students than the district schools, since they get to choose their student population from the total available student population.  Because the bin that THS is in is comprised mostly of charter schools, the scores of THS students are not that different from the other schools in that same bin.  However, they still perform above the mean for their bin.

## Scores by school type
Below is a DataFrame of the scores sorted by school type- district and charter. THS is of course, a charter school.

![Alt_text](https://github.com/Nickguild1993/School_District_Analysis/blob/master/Cleaned_school_type_DF.png)

As the above visual shows, there is a wide discrepency in scores between district schools and charter schools.  Charter schools, by their nature, are at an advantage since they get to pick the best students from the total student population, which not only boosts their scores, but reduces the scores at the district schools that those children would've normally attended.  While both the reading and math scores at charter schools are higher, the **math scores** really show the difference between the two types, with the average math score at charter schools being 6.5 points higher (83.5 to 77.0) and the percentage of students passing math with an even higher differential of 27% (94% passing math charter schools compared to only 67% passing at district schools). The scores at THS are in line with those scores of other charter schools, with the differences being only a few hundreds of a percentage.

# Summary
Overall, replacing the in question scores with NaNs doesn't really change much.  Because all of the challenge analysis for performance across school type, school size, school spending, among others, was done with only looking at the scores of the 10th-12th graders of THS, which were in line with the scores of THS *before* you replace the 9th grade scores with NaNs.  The main change was of course in scores by grade, because instead of having an average score of 83.6 for math and 83.7 for reading for THS ninth graders, you have NaNs in place of both now.  What is curious though is that the scores of the 9th graders at THS are not noticeably higher than both the scores of the 10th-12th graders at THS, nor the scores for other **charter** schools 9th graders.  So if they're truly cheating, either they are so bad at it that they didn't statistically raise their scores, or every student at charter schools is cheating, making it impossible to make an apples to apples comparision, or perhaps, they didn't cheat at all. 

Again, since the analysis in the challenge was done with scores for THS *after* the ninth grade scores had been excluded, and thus we were only examining the three older grades scores at THS, there just weren't that many differences.  There are changes, but again they're small.  For example, in the original school district analysis, Thomas High School had an overall passing percentage of 91.0%, and in the cleaned version, the schools passing percentage was 90.7%.  A difference to be sure, but a small one.  

The average math score at Thomas High School went from being 83.42 down in the original DataFrame that includes all students at THS to 83.35 for when you're only examining the 10th-12th grade scores.  So here again the scores are very consistent at THS across grade level.  For metrics like performance by school size and school spending per student, those didn't change because Thomas High School has the same amount of total students (1,635) in both the original and the cleaned version of the school district analysis, because again, we're not replacing the 9th graders who're under suspicision, just *their scores*.  Even if we did pretend that those students didn't go to THS, the school would still have 1,174 students, which would keep them in the same bin for school size (1000-2000 students).
