# Data Cleaning Log

#### Data Set Description 
|Field|Description|
|---:|:---|
|Country|Country|
|Year|Year|
|Status|Developed or Developing status|
|Life expectancy|Life Expectancy in age|
|Adult Mortality|Adult Mortality Rates of both sexes (probability of dying between 15 and 60 years per 1000 population)|
|infant deaths|Number of Infant Deaths per 1000 population|
|Alcohol|Alcohol, recorded per capita (15+) consumption (in litres of pure alcohol)|
|percentage expenditure|Expenditure on health as a percene of Gross Domestic Product per capita(%)|
|Hepatitis B|Hepatitis B (HepB) immunization coverage among 1-year-olds (%)|
|Measles|Immunization, measles (% of children ages 12-23 months)|
|BMI|Average Body Mass Index of entire population|
|under-five deaths|Number of under-five deaths per 1000 population|
|Polio|Polio (Pol3) immunization coverage among 1-year-olds (%)|
|Total expenditure|General government expenditure on health as a percene of total government expenditure (%)|
|Diphtheria|Diphtheria tetanus toxoid and pertussis (DTP3) immunization coverage among 1-year-olds (%)|
|HIV/AIDS|Deaths per 1 000 live births HIV/AIDS (0-4 years)|
|GDP|Gross Domestic Product per capita (in USD)|
|Population|Population of the country|
|thinness 1-19 years|Prevalence of thinness among children and adolescents for Age 10 to 19 (%)|
|thinness 5-9 years|Prevalence of thinness among children for Age 5 to 9(%)|
|Income composition of resources|Income composition of resources (HDI)|
|Schooling|Number of years of Schooling(years)|


#### Immunizing factors 

##### Features for predicting (X) - only 2015 
###### 1. Hepatits B 
- Data Description: Hepatitis B (HepB) immunization coverage among 1-year-olds (%)
- Missing Values: 9
    - Scandinavian countries that are missing are: Denmark, Finland, Iceland, Norway, Sweden and United Kingdom
    - **Why missing?:** Based on WHO, they would consider hepatitis B is not a treathening public health problem, so it is not been given to infanct as a universal vaccination. Vaccination only been given to the well-define risk group [[1]](https://www.euro.who.int/en/health-topics/disease-prevention/vaccines-and-immunization/vaccine-preventable-diseases/hepatitis-b)
    - Asian Country: Japan 
    - **Why missing?:** Japan started to implement Hepatitis B to infants in 2016 [[2]](https://www.thelancet.com/journals/laninf/article/PIIS1473-3099(16)30463-7/fulltext), so any data before that will be null
    - Other countries : Hungary, Slovenia, Switzerland
    - **Why missing?:** implement on older children and teenagers [[3]](https://www.euro.who.int/en/health-topics/disease-prevention/vaccines-and-immunization/news/news/2017/07/who-european-region-moving-closer-to-control-of-hepatitis-b)
- Handling Missing values: we will put it as 0 for the Null data. That means no vaccination are given in those countries

###### 2. Measles 
- Data Description: Measles - number of reported cases per 1000 population
- Missing Values: 0 
- ***Need to do***: standarize to % like other features. Since it is the number of reported cases per 1000 population, we can assume that people that does not get measles have the immunity. 
- Handling Missing Values: Got data from The World Bank for that year. 
###### 3. Polio
- Data Description: Polio (Pol3) immunization coverage among 1-year-olds (%)
- Missing Values: 0
###### 4. Diptheria 
- Data Description: Diphtheria tetanus toxoid and pertussis (DTP3) immunization coverage among 1-year-olds (%)
- Missing Values: 0 


##### Prediction output (y) - Immunization Factors
###### Life Expectancy 
- this is the prediction values in age 
- Data Description: Life Expectancy in age
- Missing Values: 10
- Accuracy of the prediction : 0.57

#### Social Factors 
##### Features for predicting (X) - only 2015 
###### 1. Income and wealth ( income composititon of resources )
- Data Description: Human Development Index [0-1] (HDI)
    - Based on UN Development Programme, it is the "summary measure of average achievement in key dimensions of human development: a long healthy life, being knowledgeable and have a decent standard of living" [[4]](http://hdr.undp.org/en/content/human-development-index-hdi)
###### 2. Education (Schooling)
- Data Description: Number of years of schooling 
###### 3. Habits (Alcohol)
- Data Description: Alcohol, recorded per capita (15+) consumption (in litres of pure alcohol)
- Missing data: almost all of the data missing in the year 2015. 
- Handle data: I download the alcohol consumption from the world bank and they have much complete data. Because the country name are not same for example in Kaggle data USA is listed as United States of America and world bank data only used United State. Previoulsy I merged with population data from world bank, where all the country merge correctly. I did the same merge again but now I dont need the population but I need the country code. With the country code, now I am able to use the world bank data on alcohol consumption. 

Data Handling: 
1. check for missing values 
2. Since each of the data are measure with different units, so the data will be standardize before send into the model 

##### Prediction output (y) - Social Factors 
###### Life Expectancy 
- this is the prediction values in age 
- Data Description: Life Expectancy in age
- Missing Values: 0
- Accuracy of the prediction : 0.82

#### Economic Factors 

##### Features for predicting (X) - only 2015 
###### 1. GDP 
- Missing Values: 29 missing values
- I used the data from World Bank and replace the whole data column. 
- There are still missing data from dataset, so I each missing data is 0 

###### 2. Status (Develop or developing)
-  Need label encoder to change it to numbers 

###### 3. Health expenditure (% GDP) 
- In the dataset, it has 2 feature that indicate the health expenditure. There are a lot of missing data in Total expenditure and the usability of percentage expenditure is low, due to some data are more than 100 since it is suppose to be a percentage value. 
- Handle data: I got the current health expenditure from World Bank Database, there are still some missing values but not as much as the orginal dataset, all the missing data are replaces with 0





