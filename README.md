# ENG2112 PA4


<b>Data Wrangling and Data Visualization <b>

For the problem assignment, we were given a CSV file to use to conduct a series of problems and conditions to find certain results that are needed.

The CSV file contained a data frame of students that had a category for gender, track, and hometown, with their grades in MATH, ELECTRONICS, GEAS, and COMMUNICATION.

To access the CSV file, I used the code:
``` python
board = pd.read_csv('board2.csv')
```
This accesses the CSV file and assigns it to a variable, which was 'board'

<b>First Problem<b>

For the sample problem, we were asked to code to group and index that fit into a certain condition:
'Vis = [“Name”, “Gender”, “Track”, “Math<70”]; hometown is constant as Visayas'

To break down the list to fit the conditions, first is to narrow it by the hometown 'Visayas'

I used: 
``` python
board.loc(board['Hometown'] == 'Visayas') #the loc code locates the within the entire data from for a set category for a set condition.
```
This code looks through the category of Hometown to look for the students who have Visayas as their hometown.

To narrow down the students who have Math <70, I used:
``` python
board.loc[(board['Math'] <70)
```
This locates the students who have grades of Math that are less than 70.

Finally, for the code that outputs the Name, Gender, Track, and Math score. I used:
```python
['Name', 'Gender', 'Track', 'Math']]
```
This outputs the categories that are inside the bracket

For the full code: 
```python
Vis = board.loc[(board['Math'] <70) & (board['Hometown'] == 'Visayas'), ['Name', 'Gender', 'Track', 'Math']]
```


<b> For the two problems, it's the same line of code just with different Conditions <b>

For the Instru Problem, it was asked to track the students who have the track of Instrumentation and the hometown of Luzon, that has a condition of their electronics grade greater than 70.
```python
Instru = board.loc[(board['Track'] == 'Instrumentation')& #tracks the students with the Intrumentation track
 (board['Hometown'] == 'Luzon') & #tracks the students that have the hometown of Luzon
(board['Electronics']>70), #tracks the students who have an electronics grade greater than 70
['Name', 'GEAS', 'Electronics'] #These categories will be the ones that will be output when u run the code.
```
Setting the code to the variable 'Intru'

For the next problem, it was asked to track students who have their hometown as Mindanao and their gender as female, while having a grade average that is >= 55

For the specific problem, it is asked to have an average, which wasn't shown in the CSV file. Meaning we have to make an average category to calculate the average grade of each student.

``` python
board['Average'] #' board['Average']' creates a category of the dataframe that is named 'Average'
board[['Math', 'GEAS', 'Electronics', 'Communication']].mean(axis=1) #this computes the mean of Math, GEAS, Electronics, and Communications combined, while axis =1 puts the new category in a column
```
For the complete line of code
```python
board['Average'] = board[['Math', 'GEAS', 'Electronics', 'Communication']].mean(axis=1)
```
Now to solve the problem:
```python
Mindy = board.loc[(board['Gender'] == 'Female') #locates the students that have Female as their gender
 & (board['Hometown'] == 'Mindanao') #locates the students that have Mindanao as their Hometown
 & (board['Average'] >= 55) #locates the studnets that have an Average >=55
, ['Name', 'Track', 'Electronics', 'Average']] #the line of categories that will be output when you run the code.
```
This problem was set into the variable 'Mindy'


<b> SECOND PROBLEM <b>

It was asked to create a visualization of how different features contribute to the average grade. The features were that if the chosen track, the hometown, or the gender contributed to a certain amount of grade.

To apply visualization, we must import matplotlib using:
```python
import matplotlib.pyplot as plt
```

Now, to track a certain feature for the graph, I used:
```python
track_avg = board.groupby('Track')['Average'].mean()
gender_avg = board.groupby('Gender')['Average'].mean()
hometown_avg = board.groupby('Hometown')['Average'].mean()
```
The code, groupby, groups up a certain category/feature that applies to the graph. 
For example, you place Track in groupby, only the track will be tracked in the graph for the grade average.

To set the size of the graph:
``` python
plt.figure(figsize=(8,5))
```

To set the graph into a bar graph:
```python
track_avg.plot(kind="bar")
gender_avg.plot(kind="bar")
hometown_avg.plot(kind="bar")
```

To set the title of the graph and the labels for the x and y axis:
```python
plt.title('Average Sources by Gender') #This sets the title of the Graph
plt.ylabel('Average score') #This sets the label of the y axis
plt.xlabel('Gender') #This sets the label of the x axis
```

To set the x-axis horizontally:
```python
plt.xticks(rotation=0)
```
This code uses the rotation in degrees, which is why the x label will be at 0 degrees, therefore horizontal.


To show the codes combined:

For Track:
```python
track_avg = board.groupby('Track')['Average'].mean()

plt.figure(figsize=(8,5))
track_avg.plot(kind="bar")
plt.title('Average Sources by Track')
plt.ylabel('Average score')
plt.xlabel('Gender')
plt.xticks(rotation=0)
plt.show()
```
For Gender:
``` python
gender_avg = board.groupby('Gender')['Average'].mean()

plt.figure(figsize=(8,5))
gender_avg.plot(kind="bar")
plt.title('Average Sources by Gender')
plt.ylabel('Average score')
plt.xlabel('Gender')
plt.xticks(rotation=0)
plt.show()
```
For Hometown:
``` python
hometown_avg = board.groupby('Hometown')['Average'].mean()

plt.figure(figsize=(8,5))
hometown_avg.plot(kind="bar")
plt.title('Average Sources by Hometown')
plt.ylabel('Average score')
plt.xlabel('Hometown')
plt.xticks(rotation=0)
plt.show()
```
