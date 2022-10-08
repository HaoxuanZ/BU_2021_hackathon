# BU_2021_hackthon
**Exploratory Data Analysis**

Data Cleaning

-   Missing Values
-   Type:
-   MCAR(Missing completely at random): These values do not depend on any other features.
-   MAR(Missing at random): These values may be dependent on some other features.
-   MNAR(Missing not at random): These missing values have some reason for why they are missing.
-   Method: drop the missing values from columns or rows.

Univariate Analysis

![](https://github.com/HaoxuanZ/BU_2021_hackthon/blob/main/Picture/UA_1.png)

-   For DOR dataset:
1.  dor['DOR Income Per Capita'] = dor['DOR Income Per Capita'].replace('\$', '').replace(',', '').astype('float')
2.  df_dor = dor.groupby(['County'])['DOR Income Per Capita'].mean().to_frame()
3.  df_dor.sort_values(by=['DOR Income Per Capita'], ascending=False).plot.barh()
4.  plt.show()
-   Group by County, get the average income per capita

![](https://github.com/HaoxuanZ/BU_2021_hackthon/blob/main/Picture/UA_2.png)

Bivariate Analysis

-   For laborforce dataset:
1.  df_lf = lf.groupby(['Year'])['Unemployment Rate'].mean().to_frame()
2.  df_lf = df_lf.sort_values(['Year'])
3.  plt.plot(df_lf)
4.  plt.title('Average Unemployment Rate In MA By Year', fontsize=14)
5.  plt.xlabel('Year', fontsize=14)
6.  plt.ylabel('Unemployment Rate', fontsize=14)
7.  plt.show()

![](https://github.com/HaoxuanZ/BU_2021_hackthon/blob/main/Picture/BA_1.png)

-   This chart shows the relationship between total amount and year.
-   On y-axis, we show the amount of net sale in the way of scientific notation, and the x-axis shows the year name.
-   As we can see, the total amount of sales has raised up gradually from year to year until year of 2020. It went down from 2020 to 2021, back to the level of year of 2019.

![](https://github.com/HaoxuanZ/BU_2021_hackthon/blob/main/Picture/BA_2.png)

-   For this part, we tried to find out if there are any stores with unusually high sales.
-   As to solve this question, we are wondering that maybe there will be some extreme values in each year’s sales data. So, we use the box plot to find out if there are any extreme value in 2017’s data.
-   Obviously, there is an extreme value on the box plot.

![](https://github.com/HaoxuanZ/BU_2021_hackthon/blob/main/Picture/BA_3.png)

-   At this part, we just full joint each year’s Net Sales part, and plot them with scatter plot.
-   As we can see on the plot, there are five extreme values total for these five years

![](https://github.com/HaoxuanZ/BU_2021_hackthon/blob/main/Picture/BA_4.png)

-   This part asks us to find out how does the spending vary from town to town. So, we tried to plot the distribution of both absolute numbers and per-capita numbers. We import the dataset and keep the variables of interest and plot the distribution of each using seaborn displot function.
-   The distribution of town-to-town spending is right skewed, most of the data of DOR income are concentrated at 0-50B and most of the data of DOR Income Per Capita are concentrated around 50000. There are also some extreme values for each part.

![](https://github.com/HaoxuanZ/BU_2021_hackthon/blob/main/Picture/BA_5.png)

-   This part we want to find out if there exist some relationship in lottery sales volume of each location with unemployment rate, DOR income per capita, and education level. By this assumption, starting with the anomaly – Methuen, then compared with a different location.
-   The sales volume had a sharper increasing rate during 2019- 2020 pandemic unemployment hikes. And Methuen has relatively low education level with most proportion of the High school graduation and lower bachelor's graduation level. The income per capita is in the 25% to 50% quantile which is also relatively low among whole Massachusetts

![](https://github.com/HaoxuanZ/BU_2021_hackthon/blob/main/Picture/BA_6.png)

![](https://github.com/HaoxuanZ/BU_2021_hackthon/blob/main/Picture/BA_7.png)

-   We selected a high-Income per capita location –Norwell and compared the same metrics with Methuen.
-   Norwell had in total lower sales volume compare with Methuen. But income per capita is 3 times than Methuen, and the greatest proportion of education level are bachelor and master degree. The lottery purchase is slower during the 2019 – 2020 unemployment hikes.

![](https://github.com/HaoxuanZ/BU_2021_hackthon/blob/main/Picture/BA_8.png)

Regression

-   First, we started with selecting variables in education level and unemployment table then merge with the aggerated lottery sales table with municipality as the key.
-   Second, we picked 6 variables to make a separate scatter plot with target value – lottery purchase per capita. In each scatter plot , we seem have

    Unemployment -- positive correlation

    Income per capita -- nonlinear correlation

    Bachelor degree and higher degree -- negative correlation

    High school degree and lower degree -- positive correlation

    Labor force – uncorrelated

    DOR code (area) – uncorrelated

![](https://github.com/HaoxuanZ/BU_2021_hackthon/blob/main/Picture/RE_1.png)

-   By creating linear regression and applied with ordinary least squares as the first filter, and VIF as the second filter to find the best fitted independent variables for the model.

![](https://github.com/HaoxuanZ/BU_2021_hackthon/blob/main/Picture/RE_2.png)

Final Regression Decision

-   Removed all statistically insignificant variables and remain unemployment rate, bachelor degree and higher degree as independent variables in linear regression model.
-   However, model had a low R-squared and adjust R-square which indicates that independent variables could not explain for the dependent variables. The case may not be suitable for a simple linear regression model. Then exploring the next stage of classification model.

![](https://github.com/HaoxuanZ/BU_2021_hackthon/blob/main/Picture/RE_3.png)

Classification

![](https://github.com/HaoxuanZ/BU_2021_hackthon/blob/main/Picture/CL_1.png)

Final

![](https://github.com/HaoxuanZ/BU_2021_hackthon/blob/main/Picture/Fianl_1.png)
![](https://github.com/HaoxuanZ/BU_2021_hackthon/blob/main/Picture/Fianl_3.png)
![](https://github.com/HaoxuanZ/BU_2021_hackthon/blob/main/Picture/Fianl_2.png)
![](https://github.com/HaoxuanZ/BU_2021_hackthon/blob/main/Picture/Fianl_4.png)
