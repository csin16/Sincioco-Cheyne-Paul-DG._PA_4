_Cheyne Paul DG. Sincioco-2ECEA_PA-4_

_PA#4 DATA WRANGLING AND DATA VISUALIZATION_

# __About the Programming Assignment__
This programming assignment is about simplifying large data sets and producing a visualization to help reveal patterns and trends faster. This task requires us to perform different functions to reveal specific elements and create a visualization to identify if a certain feature affects the result.

------------------------------------------------------------------------------------------------------------------------------------------------------
__ECE BOARD EXAM PROBLEM: Using data wrangling and data visualization techniques with storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.__

__1.  a. Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as
Instrumentation and hometown Luzon__

__Code:__
```
import pandas as pd                 #Imports pandas as the variable pd
df = pd.read_excel('board2.xlsx')   #Loads the board2 file 
```
Pandas was imported as pd since the problem requires dataframes. This problem shows the use of loading a __.xlsx__ file in Python. With the use of __pd.read_excel()__, the Excel file was loaded and was stored in df.

__Code:__
```
Instru = df.loc[(df['Electronics'] > 70) &
        (df['Hometown']=='Luzon') &
        (df['Track']=='Instrumentation'), ['Name', 'GEAS', 'Electronics']] 
         display('a.)', Instru)
#Locates the element's electronics grade if it is higher than 70, their hometown is Luzon, and their track is instrumentation
#Also displays their name, and the subjects, GEAS and Electronics
```
Then, to locate a specific element or feature, use __df.loc__. The code __df.loc__ was used in this problem to find a specific feature. In this problem, their hometown must be Luzon, and their track must be Instrumentation. Their name, GEAS, and electronics were displayed.

__Example Output:__

<img width="333" height="156" alt="Image" src="https://github.com/user-attachments/assets/0d312a02-83d3-4d3c-a8ec-8e9a159842be" />

-----------------------------------------------------------------------------------------------------------------------------------------------------
__b. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is
constant as Mindanao and gender Female__

__Code:__
```
subs = ['Electronics', 'GEAS', 'Math', 'Communication'] #Set a single variable for all the features/subjects
df['Average'] = df[subs].mean(axis=1)                   #Gets the average of the subjects per name
```
Next up, __subs[]__ was used to store all features into one variable. Then __df['Average']__ was the name of the index, __df[subs].mean__ is a function to get the average of all the subjects in subs, and lastly, __(axis=1)__ was used to put all the values in a column.

__Code:__
```
Mindy = df.loc[(df['Average'] >= 55) & 
        (df['Hometown']=='Mindanao') & 
        (df['Gender']=='Female'), ['Name', 'Track', 'Electronics', 'Average']]
        display('b.)' , Mindy)
#Locates the elements whose average is higher than or equal to 55, their hometown is Mindanao, and they are female
#Also displays their name, track, electronics subject, and their average
```
The code __df.loc__ was used again to locate the specific features, such as their Hometown must be Mindanao, and their Gender must be Female. Then their name, track, electronics, and average grade were displayed.

__Example Output:__

<img width="332" height="201" alt="Image" src="https://github.com/user-attachments/assets/805a2d05-6f30-42e5-a035-24c2b33c11ce" />

-----------------------------------------------------------------------------------------------------------------------------------------------------
__2. Create a visualization that shows how the different features contribute to the average grade. Does chosen track in college, gender, or hometown contribute to a higher average score?__

__Code:__
```
import matplotlib.pyplot as plt #Import matplotlib Library as variable plt
```
The __matplotlib.pyplot__ is a code for creating visualizations. It was imported as the variable plt.

__Code:__
```
subs = ['Electronics', 'GEAS', 'Math', 'Communication']      #Set a single variable for all the features/subjects
df['Average'] = df[subs].mean(axis=1)                        #Gets the average of the subjects per name
```
The list __subs=[]__ was used to store all features. Then, __df['Average']__ was the name of the index, __df[subs].mean__ is a function to get the average of all the subjects in subs, and lastly, __(axis=1)__ was used to put all the values in a column.

__Code:__
```
AveragebyGender = df.groupby('Gender')['Average'].mean()        #Groups the data depending on the gender and computes its mean
AveragebyTrack = df.groupby('Track')['Average'].mean()          #Groups the data depending on the track and computes its mean
AveragebyHometown = df.groupby('Hometown')['Average'].mean()    #Groups the data depending on the hometown and computes its mean
```
The code __df.groupby()__ to group the variables by their features. Then, the code __['Average'].mean()__ was used to get their corresponding mean.

-----------------------------------------------------------------------------------------------------------------------------------------------------
__Code:__
```
plt.figure(figsize=(6, 5))                             #Width and length of the plot
plt.title('Average by Gender')                         #Sets the title of the graph as "Average by Gender"
plt.ylabel('Average Score')                            #Sets the label of the y-axis as "Average Score"
plt.xlabel('Gender')                                   #Sets the label of the x-axis as "Gender"
plt.bar(AveragebyGender.index, AveragebyGender.values) #X as the gender and y as the average, shows the average based on their gender
```
The code __plt.figure(figsize=(6, 5))__ is a function that was used to determine the size of the plot, by giving its width and length. The codes __plt.title()__,__plt.ylabel()__, and __plt.xlabel__ are used to set the title and the labels of the graph. __plt.bar(x,y)__ was used to display the graph. The code __.index__ will return the feature or the category as the values for the x-axis, and __.values__ will return the computed average for each feature as the values for the y-axis.

__Example Output:__

<img width="531" height="457" alt="Image" src="https://github.com/user-attachments/assets/4f6b1092-7f11-4613-a030-7c70721fba78" />

-----------------------------------------------------------------------------------------------------------------------------------------------------
__Code:__
```
plt.figure(figsize=(6, 5))                           #Width and length of the plot
plt.title('Average by Track')                        #Sets the title of the graph as "Average by Track"
plt.ylabel('Average Score')                          #Sets the label of the y-axis as "Average Score"
plt.xlabel('Track')                                  #Sets the label of the x-axis as "Track"
plt.bar(AveragebyTrack.index, AveragebyTrack.values) #X as the track and y as the average, shows the average based on their track
```
The code __plt.figure(figsize=(6, 5))__ is a function that was used to determine the size of the plot, by giving its width and length. The codes __plt.title()__,__plt.ylabel()__, and __plt.xlabel__ are used to set the title and the labels of the graph.  __plt.bar(x,y)__ was used to display the graph. The code __.index__ will return the feature or the category as the values for the x-axis, and __.values__ will return the computed average for each feature as the values for the y-axis.

__Example Output:__

<img width="531" height="452" alt="Image" src="https://github.com/user-attachments/assets/1d55282b-13fd-4d8b-ab5b-a6d634edebf8" />

-----------------------------------------------------------------------------------------------------------------------------------------------------
__Code:__
```
plt.figure(figsize=(6, 5))                                 #Width and length of the plot
plt.title('Average by Hometown')                           #Sets the title of the graph as "Average by Hometown"
plt.ylabel('Average Score')                                #Sets the label of the y-axis as "Average Score"
plt.xlabel('Hometown')                                     #Sets the label of the x-axis as "Hometown"
plt.bar(AveragebyHometown.index, AveragebyHometown.values) #X as the hometown and y as the average, shows the average based on their hometown
```
The code __plt.figure(figsize=(6, 5))__ is a function that was used to determine the size of the plot, by giving its width and length. The codes __plt.title()__,__plt.ylabel()__, and __plt.xlabel__ are used to set the title and the labels of the graph.  __plt.bar(x,y)__ was used to display the graph. The code __.index__ will return the feature or the category as the values for the x-axis, and __.values__ will return the computed average for each feature as the values for the y-axis.

__Example Output:__

<img width="519" height="455" alt="Image" src="https://github.com/user-attachments/assets/a5f19dd2-5d2a-4f22-bca0-39e3aebb4529" />

------------------------------------------------------------------------------------------------------------------------------------------------------
__Lessons Learned:__

This programming assignment taught me to make use of different data visualizations to analyze large data sets and identify trends faster. Also, this programming assignment taught me to make use of different functions in pandas and matplotlib in solving problems in various ways. To create visualizations and compare elements.

__Tech(s) Used:__ Jupyter Notebook
