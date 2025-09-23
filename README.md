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

``` python
board.loc[(board['Track'] == 'Instrumentation') &
board.loc[(board['Math'] <70) #locating the variables that apply to the condition like whether finding the same track or having higher grades
['Name', 'Gender', 'Track', 'Math']] #this code outputs the specific column that was categorized when you input it.
board[['Math', 'GEAS', 'Electronics','Communication']].mean(axis=1) #gets the mean of all what is inside the bracket and places it in axis 1 which mean its a column
track_avg = board.groupby('Track')['Average'].mean() #groupby groups the certain data by what variable you put on it.
plt.figure(figsize=(8,5)) #inputs the size of the graph
track_avg.plot(kind="bar") #sets up what type of graph we will use
plt.title('Average Sources by Track') #places the titles of the graph
plt.ylabel('Average score') #places the label on the y axis
plt.xlabel('Track') #place the label on the x axis
plt.xticks(rotation=0) #rotates the label horizontally
```
