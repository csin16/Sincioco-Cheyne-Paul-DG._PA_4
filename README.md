Cheyne Paul DG. Sincioco-2ECEA_PA-4

PA#4 DATA WRANGLING AND DATA VISUALIZATION

# __About the Programming Assignment__
This programming assignment is about simplifying large data sets and producing a visualization to help reveal patterns and trends faster. This task requires us to perform different functions to reveal specific elements and create a visualization to identify if a certain feature affect the result.
------------------------------------------------------------------------------------------------------------------------------------------------------
__ECE BOARD EXAM PROBLEM: Using data wrangling and data visualization techniques with storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.__

__1.  a. Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as
Instrumentation and hometown Luzon__

  __b. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is
constant as Mindanao and gender Female__

__Code__
```
import pandas as pd
df = pd.read_excel('board2.xlsx') #Loads the board2 file 
#Locates the element's electronics grade if it is higher than 70, their hometown is Luzon, and their track is instrumentation
#Also displays their name, and the subjects, GEAS and Electronics
Instru = df.loc[(df['Electronics'] > 70) & (df['Hometown']=='Luzon') & (df['Track']=='Instrumentation'), ['Name', 'GEAS', 'Electronics']] 
display('a.)', Instru)

subs = ['Electronics', 'GEAS', 'Math', 'Communication'] #set a single variable for all the features/subjects
df['Average'] = df[subs].mean(axis=1)#gets the average of the subjects per name
#Locates the elements whose average is higher than or equal to 55, their hometown is Mindanao, and is a female
#Also displays their name, track, electronics subject, and their average
Mindy = df.loc[(df['Average'] >= 55) & (df['Hometown']=='Mindanao') & (df['Gender']=='Female'), ['Name', 'Track', 'Electronics', 'Average']]
display('b.)' , Mindy)
```
__Description:__ This problem shows the use of loading a __.xlsx__ file in Python. With the use of __pd.read_excel()__, the file was loaded and was stored in df. Then, to locate a specific element or feature, use __df.loc__. __df.loc__ was used in this problem to find a specific feature. Their name, GEAS, and electronics were displayed. Next up, __subs[]__ was used to store all features into one variable. Then, .mean() was used to get the average of their subject and stored as the feature 'Average'. __df.loc__ was used again to locate the specific features and their name, track, electronics, and average grade were displayed.

__Example:__

```
Output:
'a.)'
Name	GEAS	Electronics
0	S1	75	89
7	S8	64	81
29	S30	57	81

'b.)'
Name	Track	Electronics	Average
1	S2	Communication	75	67.25
2	S3	Instrumentation	74	72.75
14	S15	Microelectronics	41	59.00
16	S17	Microelectronics	79	70.50
19	S20	Communication	60	66.50

```
------------------------------------------------------------------------------------------------------------------------------------------------------
__2. Create a visualization that shows how the different features contribute to the average grade. Does chosen track in college, gender, or hometown contribute to a higher average score?__

__Code:__
```
import matplotlib.pyplot as plt #Import matplot library as variable plt
subs = ['Electronics', 'GEAS', 'Math', 'Communication'] #Set a single variable for all the features/subjects
df['Average'] = df[subs].mean(axis=1) #Gets the average of the subjects per name

plt.figure(figsize=(8, 3)) #Width and length of the plot
plt.bar(df['Gender'], df['Average']) #X as the gender and y as the average, shows the average based on their gender

plt.figure(figsize=(8, 3))
plt.bar(df['Track'], df['Average']) #X as the track and y as the average, shows the average based on their track

plt.figure(figsize=(8, 3))
plt.bar(df['Hometown'], df['Average']) #X as the hometown and y as the average, shows the average based on their hometown
```

__Description:__ This problem shows the use of __matplotlib.pyplot__ for creating visualizations. Again, __subs=[]__ was used to store all features, and __.mean()__ was used to get the mean of all the stored features in subs. __plt.figure()__ function was used to determine the size of the plot, by giving its width and length. Then __plt.bar(x,y)__ was used to determine the x and y coordinates of the plot, which is the specific feature and its contribution to the average.  

__Example:__
```
Output:
<img width="646" height="257" alt="Image" src="https://github.com/user-attachments/assets/de0e481a-68fa-4b50-afc8-408805c1bb38" />
```
------------------------------------------------------------------------------------------------------------------------------------------------------
__Lessons Learned:__

This programming assignment taught me to make use of different data visualizations to analyze large data sets and identify trends faster. Also, this programming assignment taught me to make use of different functions in pandas and matplotlib in solving problems in various ways. To create visualizations and compare elements.

__Tech(s) Used:__ Jupyter Notebook
