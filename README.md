# ENG2112 PA4


<b>Data Wrangling and Data Visualization <b>

For the problem assignment, we were given a CSV file to use to conduct a series of problems and conditions to find certain results that are needed.

The CSV file contained a data frame of students that had a category for gender, track, and hometown, with their grades in MATH, ELECTRONICS, GEAS, and COMMUNICATION.

To access the CSV file I used:
``` python
board = pd.read_csv('board2.csv')
```


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
