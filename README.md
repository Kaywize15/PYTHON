01 CRASH DATA REPORT

02 PROBLEM STATEMENT
#This Python Dashboard visualization helps to analyze the Crash/Accident details in some part of the United State of America (USA). This Data gives a thorough research about the crash calamities in the State resulting from different Road Users at different occassions and days. Using some parameters to calculate and visualize the charts, the Chart talks about various methods in which accident occurs.

03 TASK GIVEN
#Total number of accident for each day
#Average speed for each Road user
#Total number of accident for each Road user
#Total number of accident for Gender
#Average age for each Road user
#Total number of accident for each day of week

04 LOADING OUR DATA INTO PYTHON
-Step(i)    import matplotlib.pyplot as plt
	    import pandas as pd
	    import numpy as np
-Step(ii)  Loading the Data into Python using Windows+R command (The Data format is a csv file)
	   Crash=pd.read_csv("C:/Users/\HELLO/Documents/DOCUMENTS/Crash_Data.csv")
	   Crash (This is the variable used to display the data after loading it in python)
-Step(iii) Using the command (Crash.columns) to display all the columns in the data including the hidden ones
	   (52843 rows × 23 columns)

05 SOLUTIONS TO TASK GIVEN
# Total Number of Accident for each day.
This is calculated as getting the total numbers of accident that occur during the days of the week (Monday-Friday)
The total number of accident for each day can be calculated using the "Dayweek" column with the count() function:
Firstly, a new variable will be assigned (Accident), then using the Data variable name with groupby function to group the "Dayweek" column in a tuple bracket() and using the same "Dayweek" column in a list bracket[] then dot count function to count the days.
Accident=Crash.groupby("Dayweek")["Dayweek"].count()
Accident (Calling the new variable to display the solution).
Dayweek
Friday       8665
Monday       6108
Saturday     9696
Sunday       8460
Thursday     7106
Tuesday      6145
Wednesday    6663

#Average Speed for each Road User.
Getting the average speed for each Road User, the "Road User" and "Speed Limit" column will be used.
Firstly, the "Speed Limit" column has some errors in values and data types which need to be corrected before proceeding.
Replacing the strings cell in the "Speed Limit" column: The Variable used in importing the data will be assigned to the "Speed Limit" column in a list bracket[], then equals to the data variable and the "Speed Limit" column in a list bracket[] dot replace, then in a tuple bracket() we would input the strings and errors in the "Speed Limit" column to 0 passing it into a dictionary bracket{} then using the dot astype function which is integer in a list bracket(int)to end it.
Crash["Speed Limit"]=Crash["Speed Limit"].replace({"Unspecified":0,"<40":40}).astype(int)
Crash["Speed Limit"]=Crash["Speed Limit"].fillna(0) - This functions fill in empty spaces to 0 in the "Speed Limit" column.
Then, the Average Speed for each Road User will be calculated as : Assigning a new variable for the solution (Speed), then using the Data variable name with groupby function to group the "Road User" column in a tuple bracket() and using the "Speed Limit" column as a mean in a list bracket[] then dot mean function to give the average speed for the Road User.
Speed=Crash.groupby("Road User")["Speed Limit"].mean()
Speed (Calling the new variable to display the solution).
Road User
Driver                          86.404854
Motorcycle pillion passenger    74.977961
Motorcycle rider                75.685400
Other/-9                        60.782609
Passenger                       84.062026
Pedal cyclist                   70.808989
Pedestrian                      65.869207

#Total Number of Accident for each Road User.
This is calculated as getting the total numbers of accident that occur for the different types of Road Users in the Data. We have 7types of Road Users column:
Driver, Motorcycle pillion passenger, Motorcycle rider, Other, Passenger, Pedal cyclist, Pedestrian.
The total number of accident for each Road User can be calculated using the "Road User" column with the count() function:
Firstly, a new variable will be assigned (RoadUser), then using the Data variable name with groupby function to group the "Road User" column in a tuple bracket() and using the same "Road User" column in a list bracket[] then dot count function to count the total numbers for each Road Users.
RoadUser=Crash.groupby("Road User")["Road User"].count()
RoadUser (Calling the new variable to display the solution).
Road User
Driver                          23816
Motorcycle pillion passenger      363
Motorcycle rider                 6637
Other/-9                           92
Passenger                       12269
Pedal cyclist                    1424
Pedestrian                       8242

#Total Number of Accident for Gender.
This is calculated by getting the total numbers of accident that occurs based on Genders. We have 2types of Gender and an unspecified type of Gender in the Data.
The total number of accident for Gender can be calculated using the "Gender" column with the count() function:
Firstly, a new variable will be assigned (Gender), then using the Data variable name with groupby function to group the "Gender" column in a tuple bracket() and using the same "Gender" column in a list bracket[] then dot count function to count the total numbers for each Gender.
Gender=Crash.groupby("Gender")["Gender"].count()
Gender (Calling the new variable to display the solution).
Gender
Female         15002
Male           37813
Unspecified        1

#Average Age for each Road User.
Getting the average Age for each Road User, the "Road User" and "Age" column will be used.
The Average Age for each Road User will be calculated as : Assigning a new variable for the solution (RoadAge), then using the Data variable name with groupby function to group the "Road User" column in a tuple bracket() and using the "Age" column as a mean in a list bracket[] then dot mean function to give the average age for the Road User.
RoadAge=Crash.groupby("Road User")["Age"].mean()
RoadAge (Calling the new variable to display the solution).
Road User
Driver                          41.397674
Motorcycle pillion passenger    28.311295
Motorcycle rider                35.017026
Other/-9                        36.434783
Passenger                       34.481213
Pedal cyclist                   38.610955
Pedestrian                      46.819097

#Total Number of Accident for each Day of Week.
This is calculated by getting the total numbers of accident that occurs during the Day of Week. We have 2types of Day of Week (Weekday and Weekend) in the Data.
The total number of accident for each Day of Week can be calculated using the "Day of Week" column with the count() function:
Firstly, a new variable will be assigned (DowAcc), then using the Data variable name with groupby function to group the "Day of Week" column in a tuple bracket() and using the same "Day of Week" column in a list bracket[] then dot count function to count the total numbers for each Day of Week.
DowAcc=Crash.groupby("Day of week")["Day of week"].count()
DowAcc (Calling the new variable to display the solution).
Day of week
Weekday    31066
Weekend    21777

06 PLOTTING THE DATA USING CHART
Step(i) - Using subplots function to plot a 2rows by 3columns chart with a figure size of 14 by 8.
Firstly, the charts will be represented by a figure, then assigning a new variable to the chart (CrashData) which equals to plot dot subplots function, then in a tuple bracket() the number of rows and number of columns will be indicated which equals to the figure size(legth and breadth of the whole chart).
fig,CrashData=plt.subplots(nrows=2,ncols=3,figsize=(14,8))
plt.savefig("ChartPlot.png") - (This save the display chart as a jpeg or any format)
plt.show() - (This will display the image as indicated below)
![ChartPlot](https://github.com/user-attachments/assets/00f7dfe2-b331-461a-b493-1336744c764b)

Step(ii) - Giving a title to the Chart.
Firstly, the figure which is the chart dot suptitle function, then in a tuple bracket() the name of the title will be passed in as a "STRING", using the fontsize function=30 and fontsize function to be italic and also the fontweight to be bold while the color of the title is is assigned as Black using the Hex Color Codes.
fig,CrashData=plt.subplots(nrows=2,ncols=3,figsize=(14,8))
fig.suptitle("CRASH DATA",fontsize=30,fontstyle="italic",fontweight="bold",c="#000000")
plt.savefig("ChartTitle.png") - (This save the display chart as a jpeg or any format)
plt.show() - (This will display the image as indicated below)
![ChartTitle](https://github.com/user-attachments/assets/40df8797-2aa2-4588-a0b4-e8e3cf61af1b)

Step(iii) - EACH CHARTS TITLE
Titles were given to each charts in the Subplots. The variable assigned to the Chart, then the default python figure of the chart will be in a list bracket[] dot set, a tuple bracket() will be opened which will entails title="The chart title you want to assign".
fig,CrashData=plt.subplots(nrows=2,ncols=3,figsize=(14,8))
fig.suptitle("CRASH DATA",fontsize=30,fontstyle="italic",fontweight="bold",c="#000000")
CrashData[0,0].set(title="Accident for each day")
CrashData[0,1].set(title="Average Speed")
CrashData[0,2].set(title="Accident for each Road User")
CrashData[1,0].set(title="Accident for Gender")
CrashData[1,1].set(title="Average age for each Road User")
CrashData[1,2].set(title="Accident for Day of week")
plt.tight_layout() - (This gives space in between the charts) 
plt.savefig("ChartTitless.png") - (This save the display chart as a jpeg or any format)
plt.show() - (This will display the image as indicated below)
![ChartTitless](https://github.com/user-attachments/assets/23f7735a-22f6-4aa6-864e-bb7d31f5879d)

NOTE: Before Plotting the Charts, we will need to assign some variables to each of our solutions above inorder to input them in our Chart codes.
Accident (Name=Accident.index
	  Number=Accident.values)
Speed (Name0=Speed.index
       Number0=Speed.values)
RoadUser (Name1=RoadUser.index
	  Number1=RoadUser.values)
Gender (Name2=Gender.index
	Number2=Gender.values)
RoadAge (Name3=RoadAge.index
	 Number3=RoadAge.values)
DowAcc (Name4=DowAcc.index
	Number4=DowAcc.values)

Step(iv) - PLOTTING THE CHARTS
- CHART [0,0] - Using an Horizontal BarChart, the horizontal barcharts indicates the total number of accident for each day. The Y-axis indicates the Days while the X-axis indicates the counts of accident.
The variable assigned to the chart (CrashData), then the default python figure of the first chart will be in a list bracket[] dot barh, a tuple bracket() will be opened which entails the properties of the Chart.
CrashData[0,0].barh(Name,Number,color="#00008B")
- CHART [0,1] - Using a Pie Chart, the PieChart indicates the average Speed for each Road User. 
The variable assigned to the chart (CrashData), then the default python figure of the second chart will be in a list bracket[] dot pie, a tuple bracket() will be opened which entails the properties of the Chart. The Shadow function gives the piechart a shadow while the explode function makes the piechart breaks in respect of the values assigned to each labels. The Auto Percentage display each label values in a percentage format.
CrashData[0,1].pie(Number0,labels=Name0,shadow=True,explode=[0,0.1,0,0.1,0,0.1,0],autopct="%1.0f%%")
- CHART [0,2] - Using a line Chart, the line chart indicates the total number of accident for each Road User. The Y-axis indicates the counts of accident while the X-axis indicates the types of Road Users.
The variable assigned to the chart (CrashData), then the default python figure of the third chart will be in a list bracket[] dot plot, a tuple bracket() will be opened which entails the properties of the Chart.
CrashData[0,2].plot(Name1,Number1,c="#000000")
- CHART [1,0] - Using a Pie Chart, the PieChart indicates the Total Number of Accident for Gender. 
The variable assigned to the chart (CrashData), then the default python figure of the fourth chart will be in a list bracket[] dot pie, a tuple bracket() will be opened which entails the properties of the Chart. The Shadow function gives the piechart a shadow while the Auto Percentage display each label values in a percentage format.
CrashData[1,0].pie(Number2,labels=Name2,autopct="%1.0f%%",shadow=True)
- CHART [1,1] - - Using a Scattered Chart, the scattered chart indicates the Average Age for each Road User. The Y-axis indicates the average age while the X-axis indicates the types of Road Users.
The variable assigned to the chart (CrashData), then the default python figure of the fifth chart will be in a list bracket[] dot scatter, a tuple bracket() will be opened which entails the properties of the Chart.
CrashData[1,1].scatter(Name3,Number3,c="purple")
- CHART [1,2] - Using a Bar Chart, the barcharts indicates the total number of accident for each Day of Week. The Y-axis indicates the count of accident while the X-axis indicates day of week.
The variable assigned to the chart (CrashData), then the default python figure of the sixth chart will be in a list bracket[] dot barh, a tuple bracket() will be opened which entails the properties of the Chart.
CrashData[1,2].bar(Name4,Number4,color="g")

Below shows the final Charts of the given Task.

fig,CrashData=plt.subplots(nrows=2,ncols=3,figsize=(14,8))
fig.suptitle("CRASH DATA",fontsize=30,fontstyle="italic",fontweight="bold",c="#000000")
CrashData[0,0].barh(Name,Number,color="#00008B")
CrashData[0,1].pie(Number0,labels=Name0,shadow=True,explode=[0,0.1,0,0.1,0,0.1,0],autopct="%1.0f%%")
CrashData[0,2].plot(Name1,Number1,c="#000000")
CrashData[1,0].pie(Number2,labels=Name2,autopct="%1.0f%%",shadow=True)
CrashData[1,1].scatter(Name3,Number3,c="purple")
CrashData[1,2].bar(Name4,Number4,color="g")
CrashData[0,0].set(title="Accident for each day")
CrashData[0,1].set(title="Average Speed")
CrashData[0,2].set(title="Accident for each Road User")
CrashData[1,0].set(title="Accident for Gender")
CrashData[1,1].set(title="Average age for each Road User")
CrashData[1,2].set(title="Accident for Day of week")
plt.tight_layout()
plt.savefig("CrashData.png")
plt.show()
![CrashData](https://github.com/user-attachments/assets/13ebf04f-827e-4259-8e58-db5c982d3fff)
