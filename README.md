# Kickstarting with Excel

## Overview of Project
	
Louise had written a play.  She decided to crowdsource the funding for this play through Kickstarter.  She wanted to use data to determine the best strategy to have a successful campaign.

### Purpose
	
There were a few important questions Louise had that we could answer with the data from previous campaigns
on Kickstarter.  First, she was interested in if the month a campaign was launched had any effect on its outcome.
Second, she asked if the goal amount determined outcome.  By creating charts to plot this data, Louise can easily
determine the answers to her questions.

## Analysis and Challenges
	
### Analysis of Outcomes Based on Launch Date
	
To analyze the outcomes based on launch date, a pivot table had to be utilized to accurately display the
information Louise was interested in.  By filtering that pivot table for only successful campaigns in the theater
category, we were able to create a line chart to visually represent launch date data of the campaigns Louise
was aspiring to emulate. ! [Theater Outcome Based on Launch Date] (https://github.com/neccher/Kickstarter-analysis/blob/1a90db72286b693fd3a9fb560400eb1beab6039a/Resources/Outcomes_vs_Goals.png).

### Analysis of Outcomes Based on Goals
	
In order to analyze the outcomes based on goals, we first had to divide the data into buckets based on 
how much money they set as their goal.  We had twelve buckets starting from Less Than $1000 and adding $5000 
increments until reaching the last bucket of Greater than $50000.  We then used `countifs()` to find the number
of campaigns that not only fell into a certain Goal bucket, but one that also met an outcome condition and was in
the play subcategory. As an example, the code used to find a Successful Play with a goal between $25000 and $29999
looked like this `=COUNTIFS(Kickstarter!$F:$F,"successful",Kickstarter!$D:$D,">=25000",Kickstarter!$D:$D,"<=29999"
,Kickstarter!$R:$R,"plays")`.  Once the table was filled out, we could display the data in a line chart.
! [Outcomes Based on Goals] (Resources/Outcomes_vs_Goals.png).


### Challenges and Difficulties Encountered
	
The challenge came when adapting the `countifs()` functions for the Outcomes Based on Goals analysis.  I
first tried to copy the first cell across the entire row.  However, I forgot about the importance of relative vs.
absolute references. Relative references will move the cells you are referencing in a formula as you move the
formula while absolute references will not.  Once I changed the columns in the formula to absolute references,  I 
was able to fill out the table with accurate information.

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?
	
	1. The largest jump of successful theater campaigns from one month to the next was from April to May while the
largest jump in failed campaigns was from September to October.
	2.  May had the largest gap between the number of successful and failed theater campaigns while December had the
closest.

- What can you conclude about the Outcomes based on Goals?
	
	1. Just under 70% of total projects had a goal of $4999 or less and just over 70% of those projects were
successful.

- What are some limitations of this dataset?

	1. It is fairly outdated.
	2. I would've liked to know if backers got rewards for donating.
	3. I also think it would be beneficial to know the largest and the lowest amount donated by one backer.

- What are some other possible tables and/or graphs that we could create?
	
	1. I would like to see which categories and subcategories attract the most backers.  I would create a bar
graph with categories/subcategories on the x-axis and number of backers on the y-axis.
	2. I would also like to know if longer campaigns were more conducive to a successful outcome.  I would 
divide the data into buckets of campaign length and create a line graph with campaign length as the x-axis,
percentages as the y-axis, and lines for each outcome displaying their representation of total projects.
