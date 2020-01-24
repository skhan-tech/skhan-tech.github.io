## Predicting Footbal Game Point Totals Using Machine Learning

*By: Saleem Khan*

![Players]({{ site.url }}/images/football-players.jpg)

<sub><sup>Photo by Joe Calomeni from Pexels</sup></sub>

# Background
With the NFL conference championships now complete i thought it would be timely to take a closer look at some football statistics ahead of the Super Bowl. I'm not a huge football fan but analyzing this data is a great way to get a better feel for the game and the statistics that drive it.

# Problem Statement
The objective of this exercise is to determine which team statistics have the greatest impact on the amount of total points scored during an NFL Game. This problem statement is very specific becasue I want to be able to compare my modeled output to the Las Vegas Over/Under betting line (see below).

![BettingLines]({{ site.url }}/images/betting-lines.png)

Las Vegas needs to be correct on their betting lines at least 52.4% of the time in order to break even. Therefore any model I  come up with will need to beat these odds in order to be profitable. I will be focusing on the Over/Under betting line above since this is probably the easiest number to predict. 

This sort of analysis can help for more than just betting, there are multiple consituents that can benefit from this sort of analysis:
+ NFL Teams: By analyzing point totals for the entire league and comparing their individual point totals, teams can better  adjust their player roster to improve scoring.
+ NFL Players: Players can get a better sense of how best to tackle (pun intended) their oppoents in the coming weeks.
+ Fans: Fans can better enjoy the game and have hours of commentary by knowing where their favorite teams excel or need improvement.


# Data Selection & Web Scraping
![Data Analysis]({{ site.url }}/images/Football-Columns.png)

<sub><sup>Photo by Markus Spiske temporausch.com from Pexels</sup></sub>

As I started this data analysis I had to find a reliable source for statistics on NFL games. The best provider I could find that also allowed webscraping was the [Pro Football Reference](https://www.pro-football-reference.com/) page. This site has an amazing depth of detail in the statistics they capture for each and every game.

Once i was able to identify a provider my next task was to determine a good way to get the data I needed. I wanted to look at 3 years worth of data for all 32 NFL teams. This would include all 16 regular season games as well as playoffs and Super Bowls. I decided to use the Selenium driver provided by Google (i.e. essentially a stripped down version of Chrome used for webscraping) in order to capture the data on each web page. I then needed to use a Python library called BeautifulSoup in order to pull the specific fields i needed.

After a bit of coding i was able to gather 1600 rows and 27 columns of data of data which represent each individiual game played. Each of the columns will be a potential feature in my machine learning model

![Dataset]({{ site.url }}/images/betting-lines.png)

# Exploratory Data Analysis

Once the data was identified, i had to do some basic analysis to get a better sense of what the data represents. I pulled down data for all of 2019 for this analysis. Each row within this dataset represented a unique station, unit, turnstile, date and time combination along with an entry and exit counter reading. There were over 10M entries in this dataset.

![MTA Data Sample]({{ site.url }}/images/MTA_Data_Sample.png)

The first thing i had to do to get a sense of where the street team should be deployed is to look at the yearly aggregate counts for all unique subway station entries. The graph below represents the yearly entry totals for the top 20 subway stations.

![Top 20 Stations]({{ site.url }}/images/TopTwentyStations-2019-Agg.png)

*x-axis is in 10's of millions*

**Recomendation #1**
The street team should be deployed to the top 20 stations by volume in NYC.

By far the busiest subway station in NYC is 34th St - Penn. Station. This subway station receives almost 30% more traffic than the second busiest subway station. I wanted to look at whether there were any seasonality effects for this subways station. The plot below shows a daily view of ridership for all of 2019. You will notice that subway ridership peaks during the spring and fall months but the changes over the rest of the year is negligible.

![Daily View]({{ site.url }}/images/34_ST-PENN_STA-Daily_Agg_Volume.png)

**Recomendation #2**
The street team can be deployed any time of year as seasonality is not a major factor. Most of the street team should be deployed to the 34th Street station since it handles 30% more volume than the second busiest station.

I then needed to look at the best days of the week to deploy the street team. I had a hunch that subway ridership would decrease on the weekend and increase during the work week. The image below proves this intuition. We see an ebb and flow to the ridership where peak traffic occurs between Tuesday and Thursday and wanes on Saturday and Sunday.

![Daily Turnstile View]({{ site.url }}/images/34_ST-PENN_STA-June_Agg_Volume.png)

**Recomendation #3**
Deploy street team resources during the work week specifically from Tuesday through Thursday.

The last question is whether there is a certain time of day that is ideal for reaching a bigger audience. After taking a closer look at the data we do see that there is a marked increase in traffic during specific times of the day. The peak hours seem to be between 6-10AM and 2-6PM. The image below shows this visually.

![Daily Turnstile View]({{ site.url }}/images/34_ST-PENN_STA-June_10_Agg_Volume.png)

**Recommendation #4**
Deploy the street team during peak rush hour times of 6-10AM and 2-6PM.

# Conclusion & Follow-Up
Analyzing the MTA data allowed me to arrive at some early conclusions about how best to deploy the WTWY street team resources. We have four specific recommendations that should put the organization on a good trajectory to maximize donations.

For future consideration I would need to look at the following to enhance this analysis:
  * *Social Media / GPS Data* - Include data from social media data providers which provide uniqie mobile devices travelling through a specific subway station. This will allow us to better target the female demographic that this group is interested in.
  * *Tech Hubs* - Find locations within NYC where there are tech hubs that would attract more of the demographic that this group is interested in.
  * *Demographic/Income Data* - Use US Census data to determine whether there are higher pockets of female demographics in the NYC area and also add in income data to improve likelihood of donations.
