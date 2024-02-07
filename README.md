# Chicago Crime Analysis

# Project Overview

## General Description
  The main goal of this project is to provide an in-depth analysis of crime distribution, how the frequency of crimes has changed over time, and specific district arrest rates in Chicago, [using data from cityofchicago.org](https://data.cityofchicago.org/Public-Safety/Crimes-2001-to-Present/ijzp-q8t2/data). I'll be addressing the year-over-year change in crime incidence starting with data from 2002 up until 2022, along with looking into the seasonality, or lack thereof, of crimes. Beyond that, I'll also be using S/ARIMA and other models to forecast potential crime rates using a varying range of data to assist in visualizing the change in crime rates. Additionally, I explore individual districts in Chicago to examine which crimes have disproportionally higher arrest rates and a higher rate of occurrence. For what appears to be significant outliers, I'll be doing additional research beyond the dataset itself to see if there is any knowledge to be gained; for exmaple, there is only one report of domestic abuse in the twenty two years of data collection.
  
I used Jupyter Notebook along with a number of Python libraries to perform the initial inspection, cleaning, and analysis. Some of the libraries used are Pandas, Seaborn, Matplotlib, Pmdarima, and StatsModels. Tableau was used as a method to clearly present patterns and forecasts. Each of the three Tableau dashboards display a unique perspective on both crime and arrest rates across Chicago. The first dashboard is an in depth map of reported crimes and arrests made. The user will be able to look into the specific districts to inspect which crimes are reported most frequently and where they take place. Another page addresses the seasonality of reported crime, and over the overall decrease in crime over the past 22 years. the Final page gives attention to the police districts that have far higher arrest rates for the same crimes, more attention and research will be performed on standout districts.


## Description of the Dataset

The dataset covers a 22 year period starting on January 1st, 2001 and ending on December 31st 2022. The data was extracted from the Chicago Police Department's CLEAR system. CLEAR (Citizen Law Enforcement Analysis and Reporting) does intentionally omit specific crimes and information such as all murders and exact addresses of all crimes. I'm personally excluding all 2023 reports as the dataset is subject to change causing entries to be altered as cases progress. As all information is entered by hand there are some inconsistencies that need to be resolved and additional cleaning that can be performed. There are 7.7 million rows, with each row being a reported crime, and 12 collumns. The collumns provide additional information such as: date, lattitude and longitude, location description, police district, domestic or not, if an arrest was made, and more. The dataset is comprised of roughly 29 - 33 unique crimes depending on classification. 

After a brief initial inspection and cleaning I converted the dataframe into a time series, having every day be it's own row and displaying the crimes reported on any given day. I then resampled the data to a yearly frequency, having each row represent a year, and each column the total number of crimes reported that year. 


<img width="569" alt="image" src="https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/9069447e-c4d0-4854-ae8a-f5abacf2e947">


Doing this easily allows me to investigate and display the change in reported crimes over the years.

![Change in Crimes 2001-2022](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/3009257c-04eb-49f0-b7f1-d3368ad55242)

Most crimes have seen a large decrease in frequency compared to 22 years ago. Due to the large volume of reported narcotics related crimes it is difficult to gauge the change in less common crimes. The only crime that has seen a significant increase in reports are weapons violations. There are only four other crimes that saw an increase of reports in 2022 compared to 2021. Those crimes are obscenity, interference with public officer, and criminal sexual assault which all saw only a double digit increase in reports. The fourth crime that increased were reports of a concealed carry license violation, which could fall under weapons violation.

## Data Visualization

![Total Crime Counts](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/c5729a80-ea79-4aab-b9ed-e74313b33c82) 

- Additional cleaning that can be performed: combining NON - CRIMINAL and NON-CRIMINAL, CRIMINAL SEXUAL ASSAULT and CRIM SEXUAL ASSAULT, 
- The crimes with the highest number of reports are not very surprising, although theft with 1.6 million reports and battery with 1.4 million reports occur significantly more often than the third most frequent.
- On the other side of the spectrum, there's domestic violence, with only one single report.



![Arrests in 2022](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/a027604c-ae70-4050-867a-6d3ee3774876)

- District 11 had much more arrests than any other district.
- District 31 had by far the fewest with only 9 arrests made.
- District 21 had no data, which either means there were no crimes or they weren't recorded.


![Crime by Month](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/434eba9e-8fd7-4d69-8688-c7ca12853c52)

## Modeling


![Narcotics Diagnostics](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/515cbcf7-ad5d-4c30-aeed-63ea26a13f09)

![Narcotics train test](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/7080b179-1cde-4d95-9e72-cb6d118a9db8)

![Narcotics Forecast](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/dacb4c94-0930-4868-8915-2a04a78a43a9)



![Assault Diagnostics](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/d299db09-4cf5-413e-a81a-e401b829077b)

![Assault Train test](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/2fdbbe88-5384-4e2f-b435-0a360a07b930)

![Assault Diagnostics](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/e8ced7f6-e6b2-462e-8f2b-fb933fcb7115)



## Tableau Analysis

Tableau Link:  https://public.tableau.com/views/Project3Dashboard_16995778005340/LocationsofTopCrimes?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link


![image](https://github.com/ThomasLane1820/Project-3/assets/139289105/e060f80c-39f3-4188-a2ff-a555b2962d41)
- 

![Tab Change in Crime](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/dff8437f-7bd1-43c9-a809-386b4bcf8c8b)


## Points to mention
- Offering an in-depth analysis of crime distribution and how certain crimes have changed over time []
- Brief exploration of the distribution of all crimes in Chicago. [] 
- Exploration of where certain crimes have disproportionally higher arrest rates or reports [] 
- How certain crimes have changed over time, whether it be more or less reports/arrest [] 
- How arrest rates vary per district [] 
- How certain crime counts vary per district []
- forecasting[]
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
