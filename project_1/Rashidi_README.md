# Project 1: Recommending States with Low Participation Rates in SATs for Marketing Opportunities

### By: Rashidi Norhashim (GA SG-DSI-27)

## Background

The SAT and ACT are standardized tests that many colleges and universities in the United States require for their admissions process. This score is used along with other materials such as grade point average (GPA) and essay responses to determine whether or not a potential student will be accepted to the university.

The SAT has two sections of the test: Evidence-Based Reading and Writing and Math ([*source*](https://www.princetonreview.com/college/sat-sections)). The ACT has 4 sections: English, Mathematics, Reading, and Science, with an additional optional writing section ([*source*](https://www.act.org/content/act/en/products-and-services/the-act/scores/understanding-your-scores.html)). They have different score ranges, which you can read more about on their websites or additional outside sources (a quick Google search will help you understand the scores for each test):
* [SAT](https://collegereadiness.collegeboard.org/sat)
* [ACT](https://www.act.org/content/act/en.html)

Standardized tests have long been a controversial topic for students, administrators, and legislators. Since the 1940's, an increasing number of colleges have been using scores from sudents' performances on tests like the SAT and the ACT as a measure for college readiness and aptitude ([*source*](https://www.minotdailynews.com/news/local-news/2017/04/a-brief-history-of-the-sat-and-act/)). Supporters of these tests argue that these scores can be used as an objective measure to determine college admittance. Opponents of these tests claim that these tests are not accurate measures of students potential or ability and serve as an inequitable barrier to entry. Lately, more and more schools are opting to drop the SAT/ACT requirement for their Fall 2021 applications ([*read more about this here*](https://www.cnn.com/2020/04/14/us/coronavirus-colleges-sat-act-test-trnd/index.html)).

>__SATS__

>SAT Scores range from 400 - 1600 with 2 major components, Evidence-Based Reading and Writing and Math, taking equal weightage.

>__ACT__

>Score of 23 on the ACT is above the current national average and will make you a strong applicant at many universities, but it may fall below the average score for accepted students at more selective colleges.

>ACT counts raw score per subject (total 4) and gives out a composite score based on your average scaled score (1- 36) per subject. a composite score of 36 indicates full marks.


## Problem Statement

As an advisor to CollegeBoard, inc., I am recommending to them to target certain US states to focus their marketing/lobbying efforts in order to increase SAT participation rates.

## Data Dictionary

Dataset used is in path: '../data/sat_act_overall.csv'

|Feature|Type|Dataset|Description|
|---|---|---|---|
|state|object|SAT & ACT scores from 2017 - 2019|States with Participation in SATs/ACTs from 2017 - 2019|
|sat_2017_participation|float64|SAT 2017 Average Scores|Percentage of student participation per state (2 decimal places) | 
|sat_2017_total        |float64|SAT 2017 Average Scores|Average Total SAT score per state (max. of 1600, 1 decimal place) | 
|sat_2018_participation|float64|SAT 2018 Average Scores|Percentage of student participation per state (2 decimal places) | 
|sat_2018_total        |float64|SAT 2018 Average Scores|Average Total SAT score per state (max. of 1600, 1 decimal place) | 
|sat_2019_participation|float64|SAT 2019 Average Scores|Percentage of student participation per state (2 decimal places) | 
|sat_2019_total        |float64|SAT 2019 Average Scores|Average Total SAT score per state (max. of 1600, 1 decimal place) | 
|act_2017_participation|float64|ACT 2017 Average Scores|Percentage of student participation per state (2 decimal places) | 
|act_2017_composite    |float64|ACT 2017 Average Scores|Average Composite ACT Score per state (1 decimal place) | 
|act_2018_participation|float64|ACT 2018 Average Scores|Percentage of student participation per state (2 decimal places) | 
|act_2018_composite    |float64|ACT 2018 Average Scores|Average Composite ACT Score per state (1 decimal place) | 
|act_2019_participation|float64|ACT 2019 Average Scores|Percentage of student participation per state (2 decimal places) | 
|act_2019_composite    |float64|ACT 2019 Average Scores|Average Composite ACT Score per state (1 decimal place) | 

## Summary of Data Analysis

![mean_par_both](https://user-images.githubusercontent.com/99335911/156630461-157869a6-0837-4efe-89f6-bb337a8e156d.png)

Mean participation rate for SATs has been increasing from 2017 - 2019 whereas for ACT has been decreasing over the same time frame.
CollegeBoard Inc. has been successful in their lobbying and marketing efforts over the years.

However, at present, there are opportunities that can be explored to further increase SAT’s market share.

__Focus on States with Low SAT Participation Rates__

*Table of Identified 19 US States with Low SAT Participation Rate (less than 20%) in 2017 - 2019*
|    | state        |   sat_2017_participation |   sat_2018_participation |   sat_2019_participation |
|---:|:-------------|-------------------------:|-------------------------:|-------------------------:|
|  0 | Alabama      |                     0.05 |                     0.06 |                     0.07 |
|  3 | Arkansas     |                     0.03 |                     0.05 |                     0.06 |
| 15 | Iowa         |                     0.02 |                     0.03 |                     0.03 |
| 16 | Kansas       |                     0.04 |                     0.04 |                     0.04 |
| 17 | Kentucky     |                     0.04 |                     0.04 |                     0.04 |
| 18 | Louisiana    |                     0.04 |                     0.04 |                     0.05 |
| 23 | Minnesota    |                     0.03 |                     0.04 |                     0.04 |
| 24 | Mississippi  |                     0.02 |                     0.03 |                     0.03 |
| 25 | Missouri     |                     0.03 |                     0.04 |                     0.04 |
| 26 | Montana      |                     0.1  |                     0.1  |                     0.09 |
| 27 | Nebraska     |                     0.03 |                     0.03 |                     0.03 |
| 31 | New Mexico   |                     0.11 |                     0.16 |                     0.18 |
| 34 | North Dakota |                     0.02 |                     0.02 |                     0.02 |
| 35 | Ohio         |                     0.12 |                     0.18 |                     0.19 |
| 41 | South Dakota |                     0.03 |                     0.03 |                     0.03 |
| 42 | Tennessee    |                     0.05 |                     0.06 |                     0.07 |
| 44 | Utah         |                     0.03 |                     0.04 |                     0.04 |
| 49 | Wisconsin    |                     0.03 |                     0.03 |                     0.03 |
| 50 | Wyoming      |                     0.03 |                     0.03 |                     0.03 |

The states identified in the table on the above have had low participation rates for SATs across 2017 – 2019 (less than 20%). These states can be the target of CollegeBoard’s effort in increasing market share, especially since SAT has yet to measurably penetrate these markets.

However, it may be hard to lobby at these states who may have already chosen ACT as their choice for standardized test, as seen by the high participation rate for ACTs in 2019 compared to SATs for the states from the table above.

![sat_vs_act_19_states](https://user-images.githubusercontent.com/99335911/156630705-dbcb676a-fcd2-46ed-9cf2-deac56d0068d.png)

Thus, besides waiting for current ACT contracts to expire, CollegeBoard can focus on states not exclusively contracted to ACTs instead.

__Focus on States with Overall Healthy Test Participation Rates__

![sat_act_50](https://user-images.githubusercontent.com/99335911/156630542-77abdd5e-5fab-481c-8e66-59531163c48a.png)

The graph above shows the participation rates of SATs and ACTs for 4 US states with healthy participation rates (close or more than 50% participation for both). CollegeBoard can look to make it enticing for students in those states to elect to take SATs instead of or even on top of ACTs.

Also, for the near term, recommendation for CollegeBoard, inc. is to focus their efforts on states who may have not yet have mandated for SAT to be the exclusive standardized test in their state (like Ohio, Oklahoma, Tennessee, and Idaho).[source](https://prepmaven.com/blog/test-prep/states-require-sat-act/)

__Leveraging on Successes__

![SAT_par_increase](https://user-images.githubusercontent.com/99335911/156630641-db9cc9bf-19f3-4822-a6e3-fe95c6086ac9.png)

Positive actions that contributed to the increase in participation rates of these states were:

>- Successful lobbying the states of Colorado([source](https://www.coloradokids.org/wp-content/uploads/2016/01/ACTvsSAT_FINAL.pdf)) and Illinois([source](https://www.chicagotribune.com/news/ct-illinois-chooses-sat-met-20160211-story.html)) to obtain exclusive contracts for SAT as the state’s choice for standardised test.

>- Initiatives such as ‘SAT School Days’ and test fee waivers to allow for students, especially from lower income bracket, to take the tests during their school time.([source](https://www.usnews.com/news/education-news/articles/2019-09-24/more-students-are-taking-the-sat-than-ever-before))

>- Initiatives such as partnering with Khan Academy to offer free test prep and offering fee waivers for college applications of those eligible for free or reduced-price lunch (FRPL) under the National School Lunch Program (NSLP) offer benefits to those of the lower income bracket.([source](https://www.coloradokids.org/wp-content/uploads/2016/01/ACTvsSAT_FINAL.pdf))

These initiatives should be used as leverage in gaining contracts with states to choose SAT as their choice for standardized test.

## Conclusion

Although there is an upward trend in the participation rate for SAT over 2017 – 2019, more can be done to increase market share and participation rate for SAT across the US.

These can be done by the following:
>- Focus on states with low participation rate.

>- Focus on states with healthy test participation rates and those that has no mandated/exclusive rights to ACTs.

>- Leverage on successful campaigns that have caused marked increase in participation rates in some states.



