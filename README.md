# COVID-19 & Misinformation: Analyzing Relationships with Public Opinion Survey Data
![image](https://user-images.githubusercontent.com/103600964/202260229-f11a807c-c68b-458b-b189-9d7663ba1acf.png)


Curtailing the dissemination of misinformation about COVID-19 is crucial to preventing the spread of unnecessary illness and death. To this end, it is paramount that the CDC understands what populations are most at risk for holding misinformed views. This project can be used by organizations like the CDC to target at-risk groups in case of another outbreak of viral illness like COVID-19.

This project uses survey data from the American National Election Studies Exploratory Testing Survey from April 2020. The survey garnered over 3k responses to questions concerning topics that include but are not limited to: electoral politics, social issues and matters of public health.

This notebook aims to classify if respondents are misinformed about COVID-19 based on their opinions and demographic backgrounds.

The target variable for the models is a COVID-19 misinformation score. I calculated the score by aggregating responses to two questions. The questions ask respondents if they believe COVID-19 was manufactured in a lab and if there was a publicly available vaccine at the time.

I find that respondents who lean conservative or hold ideologically conservative view points tend to be the most at risk for misinformation surrounding COVID-19.

# Disclaimer  
ThIS project deals with controversial topics and opinions. The findings from this project are not reflective of my own view points, opinions or ideas. All opinions expressed in this project come from the ANES ETS 2020 respondent pool. Moreover, the word choice for questions and variables come from the ANES dataset. The conclusions from this project are simply a product of the dataset. Additionally, many other factors can influence misinformed viewpoints. To that end, this analysis only explores correlations NOT causations. The demographic variables and opinions mentioned may not cause one to believe in misinformation. The relationships explored in this notebook are only preliminary findings of potential relationships. This research has not been peer-reviewed, nor does it come from an accredited research instiution. Do not use this notebook as a source for future research projects. Furthermore, I was not asked by the CDC to create this analysis. The CDC is an example of a stakeholder who could benefit from this analysis. I am not affilated with the CDC nor the ANES.


# Main Findings 
My analysis of the American National Election Study's Pilot Exploratory Testing Survey from April 2020 found that responses to the four questions listed below were the most influential factors in my best model. 

 * Ethno-racial Group Consciousness
    * A. This question asked respondents if they feel it is likley or unlikely that white job seekers struggle in comparission to job seekers from under-   represented groups in the market place
 * Immigration 
    * This question asked respondents how much they approved or disapproved of former President Donald Trump's immigration policies
 * Former President Barack Obama
    * This question asked respondents to rate former President Barack Obama on a feeling themometer scale of 0-100. Where 0 is cold, 50 is neutral and 100 is warm 
* Racical Resentment 
  * The ANES ETS 2020 calculated a racial resentment index by aggreating responses to multiple questions that asked respondents about their own group identity and other group identities

# Notebooks & Dataset
The notebook titled "main_notebook" includes all EDA, data cleaning and modeling required to understand the analysis. In the data folder you will be able to access to codeboom and complete questionaire the ANES ETS 2020 used. You can download the data here: [ANES ETS 2020](https://electionstudies.org/data-center/2020-exploratory-testing-survey//)

# Data Cleaning 
The CSV file labeled "anes_pilot_2020.csv" is the primary data source for this project. The dataset included responses to all 470 survey questions. In addition to questions that fielded public opinion, the questions also asked respondents for demographic information which included but is not limited to: self-reported political ideology, self-reported party identification, self-reported ethno/racial identification, sex, age, education level, location of residency, and income. I engineered a target variable labeled "covid_mis_score" which is a 0 to 1 point scale for misinformation about COVID-19. I created this variable by combining responses from two questions that asked respondents about vaccines and the origin of the novel virus. A misinformation score of 1 indicates the respondent gave misinformed answers, whereas a score of 0 designates the respondent gave informed answers. Then I used several feature selection methods to parse out which variables were the most important for my models. After I imputed the median values for missing and non-responses, I began my iterative modeling process.   


# Models 
## Baseline Model 
The dummy model classified the majority class (informed) for all respondents with a recall score of 52%

![image](https://user-images.githubusercontent.com/103600964/202254677-0ae279d2-9292-46e4-8dba-30fe9a847f98.png)

## Decision Tree 
For this model, I only used the features that appeared in all 5 feature selection algorithms. I ended up with 15 features and a recall score of 67%

![image](https://user-images.githubusercontent.com/103600964/202256465-7401b1ec-d4fb-47bc-a6d1-f057306bd71a.png)



## Best Model: Random Forest 
In my best model, I used the features which appeared in all 5 and in 4 of the feature selection algorithms. Then I used GridSearch to find the best hyperaparemters for the Random Forest. This model garnered a recall score of 71%. 

![image](https://user-images.githubusercontent.com/103600964/202259640-aeee49f2-f7e4-439b-9ba9-6caf463937b0.png)



# Recommendations
Overall, respondents who lean ideologically conservative are more at risk of believing in misinformation about COVID-19 than respondents who do not. Organizations like the CDC could be best served if they find a trusted spokesperson or figure to relay validated information to these groups. Moreover, organizations like the CDC may focus on running informative advertisement campaigns in homogenous communities. 

# Areas for Future Consideration 
For the next phase of this project I will weight the ANES data with census level data to get a more accurate distribution of demographics. Further, I could merge data from other public opinion studies and surveys on public health to investigate historical trends in scientific misinformation. 

# Repository Structure 
├── data                                 <- Data folder with ANES Data 

├── experimental_code                    <- Folder with history of all code for project 

├── README.md                            <- The README for this project 

├── SJCapstone.pdf                       <- The slide deck for presentation of this project 

├── main_notebook.ipynb                  <- The simplified notebook and overview of all steps of this project 
