# Nigeria-COVID-19-Data-Analysis-Using-Python
Data Scientist Microdegree Capstone Project

## Description:

#### A deep dive into the exploratory analysis of the impact of the corona virus alias covid19 on the economy of Nigeria

# Project Steps

## Data Collection
- loaded the required libraries
- passed the ncdc weblink to a variable
- used the request() from the request library to make a request of the html codes from the backend
- then used the beautifulsoup function to collect the html codes
- looked into the soup to fetch the chunk of codes containing the table as follows:
- collect the column names fromn the html codes
- then used a loop to fetch the table info from the hmtl codes
- then created the NCDC data frame using the pandas.DataFrame()
- created variable for each url to read the daily covid cases data set from the John Hopkins Data Repository
- used the pandas read_csv method to read the data from the repo haing passed them into a url
- also used the pandas read method to load the external data sets

## Exploring the data
- used the head() and the info to get basic information on the data

## Data Cleaning and Preparation
#### ncdc_df
- To rename the table scraped data columns I used the ncdc_df.rename()
- used the dtypes() to check the data types in each variable and discovered they are all object
- used the astype(str).astype(int) to covert the numeric variables to integers as it should be
- used the df.head() method to observe the ncdc_df data to review changes that was made
- the head() also gave me the first five rows of the data to review the changes made
#### daily covid19 cases from the John Hopkins repository
- used the df.head() to view the first five rows and discovered the data is wide format
- filtered the data for Nigeria covid data and then dropped the columns that are not needed using the df.drop() and assigning the result in a variable dlcc
- converted the data frame to a long data frame creating just 2 columns date and cases using the pd.melt()
- used the df.head() to view the data to review changes that was made
- used the df.info() to observe the data types in the data set
- used the astype(datetime64[ns]) to convert the date variable formatted in strings to datetime variable
- used the df.info() to review the changes that was made to the data set
- Repeated the procedures above for the other 2 daily cases data set
## Analysis

#### Daily Confirmed Cases
- used the df.nlargest() to find the states with the first 10 largest confirmed cases and assigned it to a variable top_10_cc
- visualized the data using the matplotlib library plt.bar()
- used the plt.title() to add a title to the plot
- used the plt.xticks() to change the rotation of the xticks label
- added x-axis label and the y-axis label with the plt.xlabel() and plt.ylabel() 
- repeated the procedures for the top 10 daily discharged cases, top 10 daily death cases and top 10 daily cases

#### Daily confirmed, recovered, and death cases
- identified the variables needed for creating my line plot for the daily confirmed lab cases
- used plt.figure(figsize=()) to increase the figure size
- used the plt.plot() to create the line plot of the daily lab confirmed cases
- added title using plt.title()
- added label using the xlabel() and ylabel() respectively
- use the plt.tight_layout() command to give the plot good layout
- repeated the procedure for the daily recovered and daily death cases

#### Daily infection rate
- calculated the daily infection rate using the pandas diff() on the cases variable to find the deirvative of the total cases
##### Viz
plot a viz to further explain the findings from the calculation of daily infection rates using the following code:
- assigned the x and y variable to the date and infection rate variable respectively
- used tbe plt.plot() to plot a line graph of the daily infection rate over time

#### Maximum infection rate
- used the pandas max() to find the maximum value of the daily infection rate variable
- I then filtered the dataframe based on the maximum value to get the corresponding date it occured

#### Relationship between the ncdc data and the external data set
- I renamed the state column in the ncdc dataset to match witb the external data set in the repo
- merged the cov_ext and the ncdc data set using the pandas.merge()
- used the head() method to view the data to preview changes made
- filted the data set for the top 10 states using the nlargest() method
#### Viz
- assigned the variables to be plotted i.e states and overall ccvi index
- plotted Overall CCVI Index and confirmed cases against states on the same axis

#### Correlation between variables
- used sns.regplot() to plot lab confirmed cases against population density to check correlation
- used the plt.title() to add title and used 
- used plt.ylabel() to add y axis label
- repeated the same procedures for vulnerability and Infection rate
- wrote the observation from the visualization

#### Effect of covid19 on the Economy
- used the pandas melt() method to covert the gdp data from a wide format to a long format
- I sorted the data frame with the year column
- I filtered the gdp data frame to obtain the GDP values for the year 2020
- filtered the data frame to obtain the index number of Q2 of 2020 gdp Q2 2020

#### Viz 1
- seaborn FacetGrid() was used to create a facetgrid and subsequently,
- map_dataframe was used to map the variable for ploting the visuals
- g.subplots_adjust() was used to adjust the plot for a title
- g.fig.subtitle() was used to add a title to the plot
- ylabel() was used to add a ylabel 
- g.set_xticklabels() was used to set the rotation
- added lagend with g.add_legend()
- i ploted a horizontal line with the plt.axhline() method

#### Viz 2
- increased the size of the plot using plt.figure()
- used fivethirtyeight for the fig style using plt.style.use
- created a barplot using the seaborn barplot()
- plotted my axhline with the value of the gdp for the 2nd quarter of 2020
- added title with plt.title()
- added the ylabel with the plt.ylabel()
- added the legend to the left top cornner using the plt.legend() method
- I saved the plot using the plt.savefig() method in matplotlib

#### Viz 3
-used plt.style.use() to introduce the style of the plot
- seaborn FacetGrid() was used to create a facetgrid and subsequently,
- map_dataframe was used to map the variable for ploting the visuals
-plt.legend() was used to add legend at the upper left side of the plot
- g.subplots_adjust() was used to adjust the plot for a title
- g.fig.subtitle() was used to add a title to the plot
- ylabel() was used to add a ylabel 
- g.set_xticklabels() was used to set the rotation
- added lagend with g.add_legend()
- i ploted a horizontal line with the plt.axhline() method

# Future Work

In the future I will include predictive analysis with required data to determine the future impact if the covid19 virus is not contained. I will also like to get sample data from authentic good sources to measure impact through consumption, investment, and international trade) and stability (central government budgets, prices, the money supply, and the balance of payments.