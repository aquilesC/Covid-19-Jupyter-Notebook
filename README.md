# Covid-19-Jupyter-Notebook
**Author**: [Aquiles Carattino](https://www.aquicarattino.com)

**Date**: 2020-04-02

Example Jupyter notebook to explore the data of the ongoing COVID-19 Pandemic. The plots you see here were last generated on 2020-04-02 10:26:11.818394. 

Data is pulled from [this repository](https://github.com/CSSEGISandData/COVID-19) which is updated regularly by the [Whiting School of Engineering of the Johns Hopkins University](https://systems.jhu.edu/research/public-health/ncov/).

To get started, head to [this notebook](https://github.com/aquilesC/Covid-19-Jupyter-Notebook/blob/master/Covid_Time_Series.ipynb)

## Figures
The notebook explores different countries and compares them, also shifting the dates to visualize the differences between countries. These are some of the Figures generated by the notebook:

### China over time
![China in Linear Scale](./Figures/China_Lin_Lin.png)

This is the evolution of the cumulative number of detected cases in China over time. In the past, there was data available regarding recoveries, and thus it was possible to make a plot like [this one](https://github.com/aquilesC/Covid-19-Jupyter-Notebook/blob/master/Figures_archive/China_Lin_Lin.png), in which you see the number of active cases. The problem is that recoveries are apparently badly reported through the world, and especially in the US. 

Since the evolution of the number of cases spans several orders of magnitude, it may be better to plot the information in logarithmic scale:
![China in Log Scale](./Figures/China_Log_Lin.png)

### Log-Log Plots number of new cases
The problem with plotting countries as a function of time is that the evolution of the pandemic is shifted. For example, in China, it started in December 2019, while the first detected cases in Europe or the US appeared only at the beginning of 2020. Plotting the number of new cases versus the number of cumulative cases can be a better way of visualizing the status of the pandemic. Let's see how **China** and **South Korea** compare to each other:

![China Korea in Log-Log](./Figures/China_Korea_Log_Log_New_Cumulative.png)

For the plot above, I am defining **new cases** as the difference in accumulated cases between two consecutive days. For these two countries, it is clear that as the epidemic progresses the number of new cases is proportional to the number of accumulated cases. Until, at some point, it drops abruptly. However, you can see that the data points are relatively noisy because of large statistical fluctuations in how new cases are reported, etc. In order to have a clear picture, instead of dealing directly with the number of new cases, I will apply a rolling window of 1 week and of 5 days, in order to smooth the data, and take into account, somehow, the variation in reporting days, etc.

![China Korea weekly-average new cases](./Figures/China_Korea_Log_Log_New_Cumulative_weekly.png)

![China Korea 5-day-average new cases](./Figures/China_Korea_Log_Log_New_Cumulative_5_days.png)

The plots above are much cleaner. The idea of having a 5-day window is that it allows seeing quicker changes, which is what people are expecting. For example, is the lockdown in Spain or Italy working? With a 5-day window, there's a better chance to see any differences. See below for more plots. 

### Europe over time
Europe as a whole is being very badly hit by the spread of nCOV19. Below you can see the cumulative number of detected cases in different countries. 

![Europe in Log Scale](./Figures/Europe_Log_Lin_01.png)

It is possible to see that the onset of the epidemic in each country happens at different times. Instead of relying on the first detected case, I shift the temporal information of the countries by the moment in which 10 cases were detected and use *Italy* as a reference. The fact I use 10 cases instead of the first is that there are a lot of statistical fluctuations when the number of cases is low. For example, one detected case may be contained and eventually recover, until a second case appears. From the plots above, it seems that once there are 10 cases detected in a country, there is no going back in the evolution of the spread. 

![Europe shifted according to Italy](./Figures/Europe_countries_shifted_log_lin.png)

To give a bit more context, we can also add the dates of lockdowns or cease of activities, using the same temporal scale than in the previous plot. Some countries, such as Italy, went into full lockdown, while some countries, such as The Netherlands, are in a state where some activities are forbidden (bars, restaurants), schools are closed, but people are not banned from going out even without reason. 

![Europe shifted according to Italy showing lockdowns](./Figures/Europe_countries_shifted_log_lin_with_lockdowns.png)

And of course, we can show the same data but in a linear scale, since log-scale may be slightly counter-intuitive for people who are just getting acquainted with exponential processes:

![Europe shifted according to Italy showing lockdowns in linear scale](./Figures/Europe_countries_shifted_lin_lin_with_lockdowns.png)

### Europe in Log-Log
We can see the evolution of the pandemic in some European countries, to try to understand what is actually happening. The plot below is done with a 5-day rolling window in order to lower the fluctuations and consider the delays in case reporting, analysis, etc. 

![Europe in Log-Log](./Figures/Europe_Log_Log_New_Cumulative_5_days.png)

Both **Sweden** and **Denmark** show the same bump, which I can't explain. It is possible to see that Italy is the only country that is actively tilting the curve. 

### Latin America
Another interesting region to observe is Latin America. Each country is showing very different evolutions over time. 

![Some Latin American countries over time in log-lin scale](./Figures/Latin_America_Log_Lin.png)

And as an example, we can see the difference between **Italy** and **Argentina**, two countries that have established complete lockdowns to prevent the spread:

![Argentina and Italy with lockdowns in log-lin scale](./Figures/Argentina_Italy_log_lin_with_lockdowns.png)

The same plot but in linear scale is very eloquent:

![Argentina and Italy with lockdowns in lin-lin scale](./Figures/Argentina_Italy_lin_lin_with_lockdowns.png)

### Latin America in Log-Log
If we plot the Latin American evolution in log-log, with a 5-day rolling window for the calculation of new cases, we obtain the figure below. I am using US data as a reference for comparing:

![Latin American countries in Log-Log new cases vs accumulated](./Figures/Latin_America_Log_Log_New_Cumulative_5_days.png)

All countries are overlapping on the same curve, and they overlap to the US curve. 

## Contribute
There are different ways of contributing to the code. If you identify a problem, you can create an [Issue](https://github.com/aquilesC/Covid-19-Jupyter-Notebook/issues) explaining what you found. If you know the solution or would like to improve any of its parts, I encourage you to create a fork of this repository, implement it and then submit a pull request. In this way, the authorship of the code will be nicely documented. 

### Useful information to gather
- Information on lockdowns or closure of activities
    I could gather some information about lockdowns or massive closure of activities in a handful of countries. This information could be systematized
    
- Number of hospitalizations
    I don't know of a source to include the number of people who are hospitalized. This is crucial to understand the evolution of the disease, not just the spread of the virus.
    
- Number of beds in hospitals
    A useful parameter to show in the figures is the total number of beds in hospitals for the countries. Especially with the number of hospitalizations, it may give insight into when countries are locking down and how much room for further expansion of the epidemic is available, globally and locally.


## LICENSE
The code is released under an MIT License. This means you can reuse it and redistribute it as you see fit. The data is released with stringent terms and conditions, and thus you should be careful with the usage you make out of it. I consider this repository an example of educational usage of the data. 