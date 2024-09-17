# Experiment 4: Data Wrangling and Data Visualization
## Course: ECE 2112 - Advanced Computer Programming and Algorithms
#### University of Santo Tomas, Electronics Engineering Department
---
## Introduction
The fourth experiment for ECE 2112: Advanced Computer Programming and Algorithms contains library name "Pandas" and also "matplotlib.pyplot". For this experiment, the programmer will deal with data wrangling and data visualization. Data wrangling (also called data munching) involves manipulation and transformation of data frames in preparation for data analytics. Data visualization is the graphical representation of any information or data.

## Intended Learning Outcomes
This experiment deals with two learning outcomes, mainly:
- To identify the codes and functions needed in cleaning and visualizing data
- To be able to apply and use the different codes and functions in creating a Python program that will be used in data wrangling and data visualization

## Summary of Problems
### Instructions: 
Download the ECE Board Exam 2 dataset found on this link: bit.ly/ECEBoardExamDataset and write a Python script/code in the Jupyter Notebook to do the given problems. You may submit your Jupyter notebook in the dedicated submission bin.

### ECE BOARD EXAM PROBLEM:
Using data wrangling and data visualization technique with storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.

### Problem 1
- Create the following data frames based on the format provided:
Example: Vis = [“Name”, “Gender”, “Track”, “Math<70”]; hometown is constant as Visayas </br></br>
Output:</br>
![image](https://github.com/user-attachments/assets/5049746d-9b20-49eb-993c-193b79fed32e)


  - Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as Instrumentation and hometown Luzon
  - Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female

- Code sample:
```
#Import panda library
import pandas as pd

#Import matplotlib's plotting framework library
import matplotlib.pyplot as plt

#Reading and loading csv file into a data frame
df = pd.read_csv('board2.csv')

#Show data in which track is contant Instrumentation, Hometown is constant Luzon, and Electronics grade is >70, then show Name, GEAS, and Electronics.
Instru = df[(df['Track'] == 'Instrumentation') & (df['Hometown'] == 'Luzon') & (df['Electronics'] > 70)][['Name', 'GEAS', 'Electronics']]
Instru

Instru.plot.bar(x='Name')

#Create a column named "Average" in which averages the grades of Math, Electronics, GEAS, and Communication.
df['Average'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)

#Show the data that have Average>=55, show Name, Track, Electornics, and Average.
Mindy = df[(df['Hometown'] == 'Mindanao') & (df['Gender'] == 'Female') & (df['Average'] >= 55)][['Name', 'Track', 'Electronics', 'Average']]
Mindy

Mindy.plot.bar(x='Name')
```
### Problem 2
- Create a visualization that shows how the different features contributes to average grade. Does chosen track in college, gender, or hometown contributes to a higher average score?

- Code sample:
```
#Import panda library
import pandas as pd

#Import matplotlib's plotting framework library
import matplotlib.pyplot as plt

#Reading and loading csv file into a data frame
df = pd.read_csv('board2.csv')

# Grouping by Gender, Track, and Hometown and calculating the average score for each category
gender_avg = df.groupby('Gender')['Average'].mean()
track_avg = df.groupby('Track')['Average'].mean()
hometown_avg = df.groupby('Hometown')['Average'].mean()

#Resize Bar Graph
plt.figure(figsize=(12, 6))

bars = plt.bar(['Male', 'Female', 'Instrumentation', 'Communication', 'Microelectronic', 'Luzon', 'Visayas', 'Mindanao'], list(gender_avg.values)+list(track_avg.values)+list(hometown_avg.values))

# Adding labels and title
plt.xlabel('Categories')
plt.ylabel('Average Score')
plt.title('Combined Bar Graph for Gender, Track, and Hometown')

# Show the plot
plt.tight_layout()
plt.show()
```
---
## How can this be related to real-life?
Python has many applications in real-life especially now that the world revolves around the use of technology. Some of the top real-life applications of Python are:
- Web Development
- Game Development
- Artificial Intelligence
- Data Science
- Audio and Visual or Image Processing

## Best Practices To Do When Coding
When coding, it is best to do practices that would help you efficiently write codes. The top 5 best practices when coding in Python are:
- Usage of descriptive variable names.
- Usage of variables for constants.
- Leaving comments and taking documentation.
- Usage of whitespace.
- Be consistent with the codes.
---
## Files Included
- Tabora-Experiment-4.ipynb: Jupyter notebook with the Python code.
- boards2.csv: Excel data for given problems.
---
## Software and Library Used
- Python (version 3.x)
- Jupyter Notebook
- pandas (Python Data Analysis Library)
- matplotlib.pyplot
---
## Author
- Carl Johnsen M. Tabora
