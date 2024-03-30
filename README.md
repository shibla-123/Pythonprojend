# Pythonprojend
Python end project
EDA is the initial and important phase of the workflow.It helps,to get a first look of the data,and help generate relevant hypothesis and decide next steps.
# importing pandas,numpy,Matplotlib,seaborn
import pandas as pd
import numpy as np
import Matplotlib.pyplot as plt
import seaborn as sns
# converting excel file into dataframe.
df=pd.read_excel('file name')
# check type
type(df)
# get preview of the data
df.head()
df.tail()
# get information about dataframe
df.info()
# list the columns
df.columns
# correct the data in the height column by random method
df['Height'].apply(lambda x:random.randint(150,180))
# display no.of rows and columns in this data set.
df.shape()
# checking duplicate values
df.nunique
# checking missing values
df.isnull
# finding summary statistics for numerical columns
df.describe()
# plotting boxplot of position,team with salary to check outliers.
# distribution of employees across each team and percentage split relative to the total no.of employees
df.groupby('Team')['Name']
team_count=df['Team'].value_counts()
percentage=round((team_count/len(df))*100,2)
visually represented distribution of employees across each team by countplot and percentage represented using pieplot.
#  Segregate employees based on their positions within the company.
df2=df.groupby('Position')['Name'].apply(list)
visually represented by using countplot.
# Identify the predominant age group among employees
Here created a new column named age group.
df['Age group']=df['Age'].apply(lambda x:'19-24' if x>=19 and x<=24 else('25-30' if x>=25 and x<=30 else ('31-35' if x>=31 and x<=35 else('36-40' if x>=36 and x<=40 else 'Null'))))
df['Age group'].value_counts().idxmax()
visually represented using count plot.
# Discover which team and position have the highest salary expenditure.
df4=df.groupby(['Position','Team'])['Salary'].sum()
df4.idxmax()
graphically represented by using boxplot
# Investigate if there's any correlation between age and salary, and represent it visually.
correlation=df['Age'].corr(df['Salary'])
visually represented by using scatterplot.
# from these analysis we gained
The data set consist of 458 rows and 9 columns.
and there are some null values existing in the data.Those null values are replaced by zeroes.
count,unique,topfreq,mean,SD,min,25%,50%,75%,max these statistical measures are obtained in a simpleway,using describe method.
By plotting box plot,this helps to find outliers.
by plotting count plot of distribution of employees across each team,
 we can understand that 'New Orleans Pelicans' is the team which has highest no.of employees.From this, number of employees in the team 'New Orleans Pelicans' has 18+ employees. The second most team which has highest no.of employees is 'Memphis Grizzlies'
 From the pie plot of percentage split we got the team'New Orleans Pelicans' has highest percentage.
The team 'Memphis Grizzlies' has second most highest percentage. The teams 'Orlando Magic and Minnesota Timberwolve' have the lowest percentages.
The position SG has more no.of employees.
C position has minimum no.of employees.
25-30 is the predominant age group.
The Team 'Los Angeles Lakers' of position 'SF' have the highest salary expenditure
The correlation between age and salary  0.205.

