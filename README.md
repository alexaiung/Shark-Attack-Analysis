# Analysis of Fatality of Shark Attacks in USA and Australia
 
This project will analyse a dataset from global shark attack file which records attacks from all the globe. The objective is to answer the hypothesis: is the fatality rate in Australia bigger than in USA, the two countries with most records? The answer could help guiding business questions in a life insurance company, for example, and could be interesting for further investigation - for example, if the answer of the hypothesis is positive, why is that so?

## Requisites
This analysis uses the following libraries: pandas, numpy and seaborn. The dataset can be found in <a href=https://www.kaggle.com/datasets/teajay/global-shark-attacks>Kaggle</a>

## Initial Exploratory Analysis and Data Cleaning
The dataset has 25723 rows, though most of it were null. Some columns were partially duplicated and not useful for the analysis and were excluded, such as 'pdf', 'href formula', 'href', 'Case Number.1', 'Case Number.2', 'original order', 'Unnamed: 22' and 'Unnamed: 23'. The empty rows were excluded too.

For better usability, two columns were renamed from 'Sex ' and 'Species ' to 'Sex' and 'Species'.

Most of the columns were composed of 'objects' dtypes. This is adequate, since most of them are non-numerical data. The main exception is the column 'Year', which is numerical and does not need correction.

The .describe() method showed us that most of the records were from the last century, though there were records since the year 0, allegedly. On further investigation, it is seen that the value 0 was given for a lot of records that did not have a clear date or that were before Christ.

Furthermore, the data is composed of basic data of the attacks, such as the location, date and time, the victim, the shark species that attacked etc.

A simple code showed the .value_counts() and unique values for all the columns, which helped to understand the format of the data in each one.

No duplicated rows were found after the exclusion of the empty ones.

## Approaching the Hypothesis
With the purpose of understanding the fatality of shark attacks in USA and Australia, the first action was to create a new binary column named 'Fatality', which would facilitate to analyse the data originated from the 'Fatal (Y/N)' column. This showed us that there were 2228 records in USA and 1338 in Australia, an amount that is easier to analyse than if we had just a few records.

The .groupby() method allowed us to summarize all the records for each country and year, as well all the fatal cases. The 'fatality_rate' column was created with the result of the division of the fatal cases by the total_cases. For better analysis, I chose to reduce the scope of the analysis to the 1900s and on.

A lineplot based on fatal_cases by year was not very useful. Seeing how there were absolute cases bigger in some years than others would not help the analysis. For that reason, I made two others lineplots: the first one registered the total cases, so we could see if there were a good amount of records for each country by years. This is important since we do not want to compare a country in a given year that has only few records with other that has thousands of it.

This first lineplot showed that there were a good amount of records in all the period, but they got more abundant since the 60s.

The second lineplot is based on the fatality rate and turned out to be useful. We can see that the fatality rate in Australia is generally bigger than in USA. We also can see that the data has better quality since the 60s, which means that more records were made by that time. For this reason, we narrowed even more the analysis to the 60s and on.

If we saw the mean fatality rate for each country from the year 1960 till 2020, we can note that the fatality rate in Australia is more than three times bigger than in the USA (0.144176 compared to 0.043554).

Trying to understand better, I analysed the mean fatality rate by decade. The first analysis was technically a mistake, since the mean was miscalculated. It was necessary to obtain all the cases, as well all the fatal cases, to correctly calculate the mean fatality rate by decade. The comparison was revealing: in all the decades, the fatality in Australia is several times bigger than in the USA!

## Conclusion
The situation of Australia is clearly worse than in the USA in terms of fatalities. This can be due several reasons which would require further analysis, but we already answered the hypothesis and could make proper decisions about, for example, how to adequately price a life insurance pertaining to shark attacks in Australia compared to the USA; or, in a scientific investigation, we would have a reason to deepen our analysis.
