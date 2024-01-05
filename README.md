# Chicago Crime Analysis

# Project Overview

## General Description
  The main goal of this project is to provide an in-depth analysis of crime distribtion in Chicago, [using data from cityofchicago.org](https://data.cityofchicago.org/Public-Safety/Crimes-2001-to-Present/ijzp-q8t2/data) and how the frequency of specific crimes have changed over time. I'll be addressing the year over year change in crime occurance starting with data from 2002 up until 2022, along with looking into the seasonality, or lack thereof, for crimes. Beyond that I'll also be using S/ARIMA and other models to forecast potential crime rates using a varying range of data to assist in visualizing the change in crime rates. Additionally exploring individual districts in Chicago to examine which crimes have disproportionally higher arrest rates along with higher a rate of occurance. For what appears to be signific outliers, I'll be doing additional research beyond the dataset itself to see if there is a anything knowledge to be gained, for exmaple there is only one report of domestic abuse in the twenty two years of data collection.
  
  I used Jupyter Notebook along with a number of python libraries to perform the intitial inspection, cleaning, and anaylsis. Some of the libraries used are pandas, seaborn, matplotlib, pmdarima, and statsmodels. **GO INTO DETAILL** 
  Using Tableau to get more complex and interactive visualizations that allows you to 







## Initial analysis

![Total Crime Counts](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/c5729a80-ea79-4aab-b9ed-e74313b33c82)

- The crimes with the highest number of reports are not very surprising, although theft with 1.6 million reports and battery with 1.4 million reports occur signifcantly more often than the thrid most frequent
- On the other side of the spectrum there's domestic violence with only one single report.

(![Change in Crimes 2001-2022](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/3009257c-04eb-49f0-b7f1-d3368ad55242)
- Most crimes have seen a large reduction in the past 22 years.
- Namely, There are far far fewer narcotics arrests made.
- There are a few crimes have seen more arrests, but most of them saw a increases in the douple or triple digits.
    - The one exception is weapons violation which saw a significant increase.

![Arrests in 2022](https://github.com/ThomasLane1820/Chicago-Crime-Analysis/assets/139289105/a027604c-ae70-4050-867a-6d3ee3774876)

- District 11 had much more arrests than any other district.
- District 31 had by far the fewest with only 9 arrests made.
- District 21 had no data, which either means there were no crimes, or they weren't recorded.

 
![image](https://github.com/ThomasLane1820/Project-3/assets/139289105/e060f80c-39f3-4188-a2ff-a555b2962d41)



Tableau Link:  https://public.tableau.com/views/Project3Dashboard_16995778005340/LocationsofTopCrimes?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link 



- Offering an in-depth analysis of crime distribtion and how certain crimes have changed over time []
- Brief epxloration of the distribution of all crimes in Chicago. [] 
- Exploration of where certain crimes have disproportionally higher arrest rates or reports [] 
- How certain crimes have changed over time whether it be more or less reports/arrest [] 
- How arrest rates vary per district [] 
- How certain crime counts vary per district []
- forecasting[]
- Data cleaning explanation and progression
- initial analysis
- Time series modeling
- Final thoughts in Jupyter
- Tableau progression, what that data revealed
- standout plots
- dashboard description


  TODO:
  - Further analysis into more crimes, namely: theft, battery, criminal, damages.
  - Additional research on certain districts based on where arrest rates are much higher, higher reports, lower arrest rates, etc.
  - Tidy up Tableau Dashboard, tell more of a story.
  - Additional reflection on the plots in Jupyter Notebook.
  - normalize the change in crime over time, or filter out extreme outliers to get a better idea of the less frequent crimes.
