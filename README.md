# DiCoDe-styleguide

Draft of a style guide for the DiCoDe-lab's research projects.
This guide will become a recommendation for new projects at the lab. 
It gives you a simple and common structure to follow and reduces the hurdles for collaborators to understand the structure of your project.
The recommendations may not generalize to all possible projects, so it is on you to decide where to follow this guide and where it makes sense to extend it or to go your own way.
If done correctly, other people will have no questions when trying to reproduce your code.


### Code

Taken from "Code Review as a Simple Trick to Enhance Reproducibility, Accelerate Learning, and Improve
the Quality of Your Team’s Research" by Vable, Diehl, Glymour.

#### Overall code format

1. Code should have a header detailing the project, the code author(s), the code reviewer, whathappens in the program (ideally with approximate line numbers), and areas where the code reviewer should pay particular attention. Code should be well-commented so that the code reviewer never needs to wonder what a section of code is doing. Code should include section headers to facilitate review (e.g. merge data sets, clean variables, create analytic sample, main paper analyses, appendix analyses).
2. Code should be ordered in the same way it is presented in the manuscript to facilitate review of both the code and the manuscript; all of the below sections should have section headers so the reviewer can find them easily. Following this format will help ensure that code is streamlined and that redundancies are removed; there should be no redundancies in the code that is sent for review. One approach is to do the data cleaning and create the analytic dataset in one file, and then perform analyses in another file; this approach is fine, just ensure that the order of the files is clear to the code reviewer. Code should generally be ordered as follows, although we acknowledge that is not always appropriate. When there are deviations from this order, they should be noted and explained.
    1. Clear your workspace at the start of the script
    2. Relevant data sets imported and merged
    3. Cleaning of variables in the same order they are presented in methods section of the manuscript, typically:
        1. Exposure
        2. Outcome
        3. Effect modifiers
        4. Other covariates (ideally cleaned in the order they are listed in the manuscript). An approach that can facilitate review is to include all the covariates in a local (Stata), macro (SAS), etc. so the code reviewer does not need to ensure all the confounders are included in each of the analytic models. This approach can also help avoid inconsistencies if the adjustment variables change over the course of the analysis. 
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
     1. to center age at 70, the centered variable could be age_c70
     2. to z-score CESD, the standardized variable could be cesd_std
     3. to trichotomize mother‟s education (assuming the variable is named momedu_yrs), the trichotomized variable could be momedu_3cat
     4. to take the natural log of income, the logged variable could be income_ln
     5. to rescale age in years to age in decades, the rescaled variable could be age_decades
4. Use standardized naming conventions in longitudinal data to indicate assessment wave or year collected, e.g. for age data collected in 1998, variable should be named age_1998 or if 1998 was the year of the 2nd wave of data collection, age_w2
5. When recoding a variable, the following approach should be used:
    a. Do not recode over original variables, always generate a new variable
    b. Name the new variable something descriptive
    c. After the variable is recoded, examine the cross-tab with the old variable, or list a few observations showing both the old and new variables to ensure the recoding has been done properly. This should be included in the code script to demonstrate the recode has been done properly to the code reviewer
    d. Apply a descriptive label to the variable (e.g. if income was inflation-adjusted to 2016 dollars, the label may be “income, inflation-adjusted to 2016 dollars”)
    
    
### Data

If you use 


### git & Github

Use git to version control all the files (except data files bigger than 100 MB).
You can use Github private repositories to share the project or the network-drives of the institute.
Github issues are a better way to discuss issues than emails.

### Directory structure



    ├── README.md          <- The top-level README for developers using this project.
    │                         The readme should contain a short general description of the project
    │                         and a high level description of what the code does and how to run it.
    │                         
    ├── data
    │   ├── external       <- Data from third party sources. Include a text file that describes
    │   │                     the origin of the data and how to get it.
    │   ├── collected      <- Data that is collected during this project.
    │   ├── interim        <- Intermediate data that has been transformed.
    │   └── processed      <- The final, canonical data sets for modeling.
    │
    ├── code               <- Code files. Naming convention is a number (for execution ordering),
    │   │                      the creator's initials, and a short `-` delimited description, e.g.
    │   │                      `1.0-jqp-initial-data-exploration`. No unused code here.
    │   │
    │   └── deprecated     <- (optional) old/redundant/unused code. This can be left there for 
    │                         reference or deleted.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in reporting
    │
    ├── references         <- (optional) Data dictionaries, manuals, and all other explanatory materials.
    └── LICENSE            <- (optional) Look at https://choosealicense.com/ to find a suitable licence.
    

### Write good readme-files

Your code should be usable and reproducible for other researchers.
That means that you have to include at least a minimal documentation.

A readme-file doesn't need to explain every detail of your code, but it should give the reader concise information about:
 * What is this code about? What does it do? Why would you need it? What is the input, what is the output?
 * How do you *use* it?
 * How do you *develop* it?

Nowadays it is standard practise to write readmes in the [Markdown format]( https://en.wikipedia.org/wiki/Markdown ). But a simple text-file is also fine.
In the next chapter I wrote a structure for a readme that you can use. 

 
#### Example Structure

##### Title of the software

Describe the essence of your software/library/code/snippet/data/whatever in one short sentence.

##### Status (optional)

If your software is not yet ready for other users or old and deprecated - add a status chapter and make this clear.

##### About

Describe what this code is about. If there is a related project or paper, link to it.

##### Installation, usage and development

How do I get started if I want to test or use the code?
What are the prerequisites? How to install them? What development environment did you use?

Include a basic example which explains the basic functionality in a simple way. You may also include more complex examples.

##### Citation

You can ask the users to cite a specific paper if they use it.

##### Licence

A licence removes uncertainty around who may use the software how.
Look at https://choosealicense.com/ to find a suitable licence.


#### External links on how to write a readme

 * https://gist.github.com/PurpleBooth/109311bb0361f32d87a2
 * https://dotdev.co/how-to-write-a-readme-that-rocks/
