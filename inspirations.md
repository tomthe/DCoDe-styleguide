# Style Guide Inspirations

### Links

* https://google.github.io/styleguide/
* https://google.github.io/styleguide/pyguide.html
* https://google.github.io/styleguide/Rguide.html
* https://style.tidyverse.org/


## Style Guide from the paper "

### Example Style Guide for Coding in Academia to Facilitate Code Review
This example Style Guide is for a relatively straightforward project of data cleaning and analysis. This
Style Guide may not generalize to other settings, for example simulation analyses, or very complex
analyses. These guidelines are not meant to be prescriptive; they represent what we consider best
practices and have evolved over the course of writing this paper.

#### Overall code format

 1. Code should have a header detailing the project, the code author(s), the code reviewer, whathappens in the program (ideally with approximate line numbers), and areas where the code reviewer should pay particular attention. Code should be well-commented so that the code reviewer never needs to wonder what a section of code is doing. Code should include section headers to facilitate review (e.g. merge data sets, clean variables, create analytic sample, main paper analyses, appendix analyses).
 2. Code should be ordered in the same way it is presented in the manuscript to facilitate review of both the code and the manuscript; all of the below sections should have section headers so the reviewer can find them easily. Following this format will help ensure that code is streamlined and that redundancies are removed; there should be no redundancies in the code that is sent for review. One approach is to do the data cleaning and create the analytic dataset in one file, and then perform analyses in another file; this approach is fine, just ensure that the order of the files is clear to the code reviewer. Code should generally be ordered as follows, although we acknowledge that is not always appropriate. When there are deviations from this order, they should be noted and explained.
  a. Clear your workspace at the start of the script
  b. Relevant data sets imported and merged
  c. Cleaning of variables in the same order they are presented in methods section of the manuscript, typically:
   i. Exposure
   ii. Outcome
   iii. Effect modifiers
   iv. Other covariates (ideally cleaned in the order they are listed in the manuscript). An approach that can facilitate review is to include all the covariates in a local (Stata), macro (SAS), etc. so the code reviewer does not need to ensure all the confounders are included in each of the analytic models. This approach can also help avoid inconsistencies if the adjustment variables change over the course of the analysis. 
  d. Define the final analytic sample, detailing who was excluded from the analytic sample and why. If data are clustered (e.g., repeated measures on the same person) describe the entire data structure. A useful approach for defining the analytic sample can be to create a variable called “eligible” that is 0 for people who are not eligible and 1 for people who are eligible. This facilitates analysis of how the analytic sample differs from the overall sample, which can be useful to include in appendix tables. 
  e. The data analysis should be conducted in the order the tables and figures are presented in the results section. The code author should confirm that every analysis includes the same number of observations, unless deviations are specifically justified and noted, to facilitate review
  f. Appendix analyses should be conducted in the order they are presented in the appendix
 3. Checks to ensure the code is working as anticipated should be included in the code script so they can be rechecked every time the code is run. This will also facilitate review by demonstrating to the code reviewer that the code is running properly. For example, when reshaping data from long to wide or vice versa, ensure that the number of unique respondents is as expected, and that the number of observations per respondent is within the expected range.
 4. Remove old or experimental code that is no longer relevant before review – all code that is reviewed should be relevant for the project.
 5. Code should run completely from top to bottom without errors or intervention from the programmer.

#### Variable cleaning conventions

 1. Use intuitive, descriptive variable names whenever possible.
 2. Dichotomous variables should be named so that 0 = no and 1 = yes, i.e., create a variable named “male” or a variable named “female” instead of a variable named “sex”
 3. For transformation of variables, attach a suffix specifying the transformation. Some possibilities are as follows:
  a. to center age at 70, the centered variable could be age_c70
  b. to z-score CESD, the standardized variable could be cesd_std
  c. to trichotomize mother‟s education (assuming the variable is named momedu_yrs), the trichotomized variable could be momedu_3cat
  d. to take the natural log of income, the logged variable could be income_ln
  e. to rescale age in years to age in decades, the rescaled variable could be age_decades
 4. Use standardized naming conventions in longitudinal data to indicate assessment wave or year collected, e.g. for age data collected in 1998, variable should be named age_1998 or if 1998 was the year of the 2nd wave of data collection, age_w2
 5. When recoding a variable, the following approach should be used:
  a. Do not recode over original variables, always generate a new variable
  b. Name the new variable something descriptive
  c. After the variable is recoded, examine the cross-tab with the old variable, or list a few observations showing both the old and new variables to ensure the recoding has been done properly. This should be included in the code script to demonstrate the recode has been done properly to the code reviewer
  d. Apply a descriptive label to the variable (e.g. if income was inflation-adjusted to 2016 dollars, the label may be “income, inflation-adjusted to 2016 dollars”)
