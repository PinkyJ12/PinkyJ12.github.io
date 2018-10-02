---
layout: post
title: "Data Visualization in Python-using Matplotlib"
featured-img: DataVisMatplotlib1
---
Matplotlib is the most popular data visualization library in Python. It allows us to create figures and plots, and makes it very easy to produce static raster or vector files without the need for any GUIs.

My this project is to find the richest country in the world on the per person basis in the sample [dataset](IntroToDeepLearning/SupervisedLeaning/VisualistionUsingMatplotlib/nations.csv)

Here,for simplicity, I compared different country’s gdp per capita to try to answer this question following the steps below :

* First,imported all necessary packages.
* Then loaded the dataset.
* Cleaned the dataset by filling in missing values.
* Aggregated values using .groupby().
* Sorted the values.
* Represented the data in line and bar plot.

Replace the missing values in 'gdp_percap' column with the median. Its always good idea to replace the values with median when there are outliers in the column.
Then calculate the mean of **Gross Domestic Product per capita** grouping them by country for all available years. After saving this value to a new variable I sorted the countries according to their gdp_percap and displayed 6 countries with the highest gdp_percap further saving this data in a new variable.

I noticed that **‘United Arab Emirates’** has the highest average gdp_percap. Having this information, I looked at ‘UAE’ in more details to find out if it’s actually the most richest country in the world on a per-person basis. This is done by plotting how the gdp_percap in ‘UAE’ has changed over time. Below is the plot showing value of GDP/capita for various years.

<p align="center"><img src="/assets/blog_images/Data_visualization/GDP-Capita as per country.png" width="65%"> </p>

As seen above, the line plot didnt gave me a good representation that I could make meaning from, so I visualized it in a barplot to get a better understanding of the data where I found the decrease in GDP from 2007 onwards. 

<p align="center"><img src="/assets/blog_images/Data_visualization/GDP-Capita as per country-bar graph.png" width="65%"> </p>

Since gdp per capita is gdp per person, I plotted UAE's gdp_percap, gdp and population on the same graph using the .subplot() function.

<p align="center"><img src="/assets/blog_images/Data_visualization/GDPCapitaGDPPopulationline1graph.png" width="65%"> </p>


For a clearer result, I plotted it’s bar graph too

<p align="center"><img src="/assets/blog_images/Data_visualization/GDPCapitaGDPPopulationbargraph.png" width="65%"> </p>

From the above plots, it was clear that inspite of increase in GDP, there was decrease in GDP per capita as there was increase in population too.


To tell how much faster their population grew relative to their gdp? I tried and compared their relative growth in a single plot by showing the population growth in the first year. I set the first year’s population to 100 as the basis of comparison, then repeat the same for gdp and gdp_percap

<p align="center"><img src="/assets/blog_images/Data_visualization/GDPCapitaGDPPopulationlinegraph.png" width="65%"> </p>

Its representation in a bar plot for clearer view.

<p align="center"><img src="/assets/blog_images/Data_visualization/GDP and population growth-firstyear-bar graph.png" width="65%"> </p>


As it can be seen, at no point did UAE's gdp ever catch up with the population growth.

To really answer this question, I went ahead and compare UAE's gdp_percap with that of another country in the top_five_countries . Here are the plots of gdp per capita growth in UAE w.r.t other countries on the same chart.

<p align="center"><img src="/assets/blog_images/Data_visualization/GDP-capita comparison b-w UAE and China.png" width="65%"> </p>

<p align="center"><img src="/assets/blog_images/Data_visualization/Gdp-capita comparison b-w UAE and Qatar.png" width="65%"> </p>


## Conclusion
As can be seen from above graphs, UAE's gdp/capita has reduced in recent years as compared to other top 5 countries but if we take overall average of all years gdp/capita of UAE is high as compared to other countries.

