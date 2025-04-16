# Chicago Crime Analysis

# Project Overview

## General Description
  The main goal of this project is to provide an in-depth analysis of crime distribution, how the frequency of crimes has changed over time, and specific district arrest rates in Chicago, [using data from cityofchicago.org](https://data.cityofchicago.org/Public-Safety/Crimes-2001-to-Present/ijzp-q8t2/data). I'll be addressing the year-over-year change in crime incidence starting with data from 2002 up until 2022, along with looking into the seasonality, or lack thereof, of crimes. Beyond that, I'll also be using S/ARIMA and other models to forecast potential crime rates using a varying range of data to assist in visualizing the change in crime rates. Additionally, I explore individual districts in Chicago to examine which crimes have disproportionally higher arrest rates and a higher rate of occurrence. For what appears to be significant outliers, I'll be doing additional research beyond the dataset itself to see if there is any knowledge to be gained; for exmaple, there is only one report of domestic abuse in the twenty two years of data collection.
  
I used Jupyter Notebook along with a number of Python libraries to perform the initial inspection, cleaning, and analysis. Some of the libraries used are Pandas, Seaborn, Matplotlib, Pmdarima, and StatsModels. Tableau was used as a method to clearly present patterns and forecasts. Each of the three Tableau dashboards display a unique perspective on both crime and arrest rates across Chicago. The first dashboard is an in depth map of reported crimes and arrests made. The user will be able to look into the specific districts to inspect which crimes are reported most frequently and where they take place. Another page addresses the seasonality of reported crime, and over the overall decrease in crime over the past 22 years. the Final page gives attention to the police districts that have far higher arrest rates for the same crimes, more attention and research will be performed on standout districts.


## Description of the Dataset

The dataset covers a 22 year period starting on January 1st, 2001 and ending on December 31st 2022. The data was extracted from the Chicago Police Department's CLEAR system. CLEAR (Citizen Law Enforcement Analysis and Reporting) does intentionally omit specific crimes and information such as all murders and exact addresses of all crimes. I'm personally excluding all 2023 reports as the dataset is subject to change causing entries to be altered as cases progress. As all information is entered by hand there are some inconsistencies that need to be resolved and additional cleaning that can be performed. There are 7.7 million rows, with each row being a reported crime, and 12 collumns. The collumns provide additional information such as: date, lattitude and longitude, location description, police district, domestic or not, if an arrest was made, and more. The dataset is comprised of roughly 29 - 33 unique crimes depending on classification. 


![Total Crime Counts](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/6a771f7a-255b-4be5-9891-cfb45c4794d7)

Some very brief data cleaning was necessary to fix some inconsistencies in how certain crimes were reported. There are, however, still a couple data points I'd like to point out and attempt to clean at a later date. The one singular domestic violence report should not have be reported as domestic violence, there is a sub-category where a crime is declared domestic or not. After attempting to look up the specifc report by the I.D and finding no luck, I reached out to CLEAR and will hopefully be able to get for information about the report. Aside from that I'd like to know more abotu the non-criminal reports. Whether or not their inclusion in this project depends on the severity of the non-criminal activity and the circumstances surrounding each case. The last primary type I'd love to have more information about would be the "other offense" type, which is the 6th most common reported crime. Knowing roughly what the other offenses could be, would help assist in both analysis and visualization. Theft and battery are by far the two most commonly reported crimes, the next nine highest reported crimes are all fairly close to one another in frequency. 


After abrief initial inspection and cleaning I converted the dataframe into a time series, having every day be it's own row and displaying the crimes reported on any given day. I then resampled the data to a yearly frequency, having each row represent a year, and each column the total number of crimes reported that year. 




<img width="569" alt="image" src="https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/9069447e-c4d0-4854-ae8a-f5abacf2e947">


Doing this easily allows me to investigate and display the change in reported crimes over the years.

![Change in Crimes 2001-2022](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/3009257c-04eb-49f0-b7f1-d3368ad55242)

Most crimes have seen a large decrease in frequency compared to 22 years ago. Due to the large volume of reported narcotics related crimes it is difficult to gauge the change in less common crimes. The only crime that has seen a significant increase in reports are weapons violations. There are only four other crimes that saw an increase of reports in 2022 compared to 2021. Those crimes are obscenity, interference with public officer, and criminal sexual assault which all saw only a double digit increase in reports. The fourth crime that increased were reports of a concealed carry license violation, which could fall under weapons violation.

It's worth looking into when exactly narcotics reports dropped off significantly. recreational consumption, possesion, and sales of cannabis products was leagalized on January 1st, 2020. While I have not yet looked into the year by year change for narcotics specifically it would be worht looking into. 




![Arrests made per district Dec 2022](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/495fa5c0-1f8f-47a9-92f1-05e5459a0ab2)


Crimes and arrest rates per district is a very interesting topic to look into, and was a big motivation for taking this project so far. While there are still dozens of way I can and will visualize the data, this simple plot still tells quite the story and inspires additional research. District 11 has by far the most arrests compared to every other district. The other outliers are district 31 and 21, both of which either no longer have an active police force, or take on more of an intelligence based role. So reports and arrests made in those districts are tallied up as a nearby districts report.
I'll explore arrest rates for specific crimes in each district much more in Tableau.

![Crime by Month](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/434eba9e-8fd7-4d69-8688-c7ca12853c52)



## Modeling


For the modeling aspect of the project I focused on using ARIMA (autoregressive moving average) and SARIMA (seasonal autoregressive moving average) models. As seen earlier there is a noticeable seasonality to the frequency of all reported crimes, however, specific crimes tend to have their own seasonality that may not line up as smoothly over time. So despite the apparent seasonality, it may not be consistent enough to provide any benefit to the model.


### Narcotics 

#### Determing the model

![Narcotics seasonality visual](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/21b8e01b-ba51-42a6-a0e6-0679184d34e7)

Many arrests saw a sharp decline in the early months of 2020, while there are multiple factors at play I think the two largest contributors are the COVID-19 pandemic and subsequent shutdown along with the legalization of marijuana in January. There is certainly is a possibility of narcotics arrests being seasonal. The seasonal component accounts for roughly 20% of the variation of the time series.

#### SARIMA model analysis

![Narcotics Diagnostics](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/383bfc9e-7f75-4377-b8d6-aa68f8d6f345)

Starting with the Standardized residuals: The plot looks like it should, the one dip in early 2020 is accounted for in the legalization of marijuana. Aside from that there is no discernible pattern or trend, which means the model has probably captured all relevant data.

Histogram plus estimated density: The kernel density estimation (KDE/orange trend line) matches the histogram fairly well. The histogram roughly follows a normal distribution aside from a few outliers.

Normal Q-Q: This plot looks great as nearly all points fall on the line except for two outliers. The outliers are visible in the histogram as well, so it should be resolvable. 

Correlogram: This plot shows autocorrelation at all lags.

![Narcotics train test](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/7080b179-1cde-4d95-9e72-cb6d118a9db8)

While the model has the general gist of the testing data it doesn't match up exactly. I'd say this should be expected considering there seems to be some reisduals are not entirely normally distributed. All in all a MAPE (mean average percent error) of 7.44% is very solid especially considering there is a clear next step. 

#### Forecasting

![Narcotics Forecast](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/dacb4c94-0930-4868-8915-2a04a78a43a9)

My SARIMA model is forecastign very little change in narcotics arrests in the first six month of 2023. Would be interesting to look back and compare the forecasted data to the recorded arrests.

### Assault

#### Determining the model

![Assault Seasonality](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/10f74635-5fcd-4235-8def-e5d7833938a2)

Despite having fairly significant residuals the seasonal component acounts for roughly 25% of the variation in the time series. I will chose a seasonal model.

#### Model Analysis

![Assault Diagnostics](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/2a296cfd-5663-4ad1-88e8-bd68f7561750)

Standardized residuals Over Time: The plot looks like it should, the major dip in early 2020 is accounted for due to the COVID lockdown. Aside from that there is no discernible pattern or trend, which means the model has probably captured all relevant data.

Histogram Plus Estimated Density: The kernel density estimation (KDE/orange trend line) matches the histogram fairly well, although, the histogram doesn't quite have an ideal distribution. Ideally the histogram would have a normal distribution, so there's need to investigate further.

Normal Q-Q Plot: This plot looks alright as nearly all points fall on the line except for one outlier. The outlier is visible in the histogram as well, so it should be resolvable. 

Correlogram: This plot shows autocorrelation at all lags.

![Assault Train test](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/2fdbbe88-5384-4e2f-b435-0a360a07b930)


#### Forecasting

![Assault Forecast](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/fbf08fab-400c-4797-8462-2f04e661db1a)




## Tableau Analysis

Tableau Link:  https://public.tableau.com/views/Project3Dashboard_16995778005340/LocationsofTopCrimes?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link


![image](https://github.com/ThomasLane1820/Project-3/assets/139289105/e060f80c-39f3-4188-a2ff-a555b2962d41)
- 
While the map looks bloated and messy as presented here, if you go to the Tableau Dashboard you'll be able to refine the metrics in multiple different ways allowing you to inspect specfic reported crimes, or specfici districts. You can also choose which year is being reflected giving more options.


![Tab Change in Crime](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/dff8437f-7bd1-43c9-a809-386b4bcf8c8b)

This is a very clear and simple representation of not only the seasonal of crime as a whole, but the seasonality that reported crimes tends to have. 
The peak months of 2015 - 2019 have far fewer reported crimes than the criminally slower months of 2001 - 2009. Signifying an incredible change occuring in Chicago.

## Points to mention
- Offering an in-depth analysis of crime distribution and how certain crimes have changed over time []
- Brief exploration of the distribution of all crimes in Chicago. [] 
- Exploration of where certain crimes have disproportionally higher arrest rates or reports [] 
- How certain crimes have changed over time, whether it be more or less reports/arrest [Partial] 
- Data cleaning explanation and progression
- initial analysis
- Time series modeling
- Final thoughts in Jupyter
- Tableau progression, and what that data revealed
- standout plots
- dashboard description


  ## Next Steps:
  - Further EDA in Juptyer
  - Adding additional comments and explanations
  - Additional research on certain districts based on where arrest rates are much higher, higher reports, lower arrest rates, etc.
  - Update Tableau
     - Give the dashboard more personality.
     - Clean and refine the data further.
     - Adding/refining visuals to reflect the goal
  - Additional reflection on the plots in Jupyter Notebook.
  - normalize the change in crime over time or filter out extreme outliers to get a better idea of the less frequent crimes.
