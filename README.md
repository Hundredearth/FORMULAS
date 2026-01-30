# FORMULAS

1. distinct/unique in the coloumns: df["DEPARTMENT_ID"].unique()

2. hash mapping: hash={}, hash[i] += 1 or  hash[i] = 1

3. sort the df by col: 
df.sort_values(by='column_name', ascending=False) 

4. 

import matplotlib.pyplot as plt #common for all

a)
simple plots : 
df.plot(kind="barh",x="Date",y="Close") #kind =line,bar,scatter,etc

b) # more than one line "  y=['y1','y2']   " 
df.plot(kind="line",x='x',y=['y1','y2'],label=["blue","red"])
 
5. 

import matplotlib.pyplot as plt #common for all

a) normal plot:
plt.figure(figsize=(10, 3))
plt.bar(df["Date"], df["Volume"])
plt.xlabel("Categories")
plt.ylabel("Values")
plt.title("Simple Bar Plot")
plt.show()

b) # more than one line  

plt.plot(x, y1, label="Series 1")
plt.plot(x, y2, label="Series 2")
plt.legend()
plt.title("Multiple Line Plot")
plt.show()

c) # bar plot
languages = ["Python", "Java", "C++", "C"]
popularity = [80, 70, 60, 50]
plt.bar(languages,popularity)
plt.show()

d) #barh->bar(h) h for horizontal
languages = ["Python", "Java", "C++", "C"]
popularity = [80, 70, 60, 50]
plt.barh(languages,popularity,color=[])
plt.show()

e) # stacked bar plot
A = [20, 35, 30]
B = [25, 32, 34]
x = np.arange(len(A))
plt.bar(x, A)
plt.bar(x, B, bottom=A)
plt.title("Stacked Bar Plot")
plt.show()

f) #multi-color bar graph
languages = ['Java', 'Python', 'PHP', 'JavaScript', 'C#', 'C++']
popularity = [22.2, 17.6, 8.8, 8, 7.7, 6.7]
colors = ['red', 'blue', 'green', 'yellow', 'purple', 'orange']
plt.bar(languages, popularity, color=colors)
plt.xlabel('Programming Languages')
plt.ylabel('Popularity (%)')
plt.title('Popularity of Programming Languages')
plt.show()


g) #scatter plot+bubble chart
scattter=x,y
bubble=x,y,sizes

x = [4,5,6,1,2,3]
y = [70,10,20,30,40,50]
sizes = [300,400,500,600,100,200]

plt.scatter(x, y, s=sizes,facecolor='none',edgecolor='red')
plt.title("Bubble Chart")
plt.show()


h)
math_marks = [88, 92, 80, 89, 100, 80, 60, 100, 80, 34]
science_marks = [35, 79, 79, 48, 100, 88, 32, 45, 20, 30]
marks_range = [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]

plt.scatter(students, math_marks, label='Math Marks', color='blue',marker='o')
plt.scatter(students, science_marks, label='Science Marks', color='red',marker='x')

plt.legend()
plt.grid(True, linestyle='--', alpha=0.6)
plt.show()



6.pivot table:
pivot_table = pd.pivot_table( df, index=['Manager', 'Region', 'SalesMan'],values='Sale_amt', aggfunc=['sum','min','max'] )

pivot_table = pd.pivot_table( df, index = ['SalesMan',"hello"]  ,values='Sale_amt', aggfunc='sum' )
#values are numeric and index are text like name 

7.random in python using numpy :
np.random.randn(10, 4)
# 10-rows amd 4-coloumns



8.colouring:

def coloring(val):
    if val>0:
        return "color:red ; background-color:yellow"
    else:
        return "color:blue ; background-color:purple"
df.style.applymap(coloring) #imp


9.checking Na:
def finding_Na(val):
    if pd.isna(val):
        return " color:blue    ;    background-color :red "
df.style.applymap(finding_Na)




10. to make Na:
df["A"][1]=np.nan

11.check null by true or false:
df.isnull()
      A       B       C       D
0	False	False	False	False
1	True	False	False	False
2	False	False	False	False



12.filling_na
def filling(val):
    if pd.isna(val):
        return np.random.randn()
    return val
df=df.applymap(filling)



13.group by:
a) #16
grouped = df.groupby('School') 
for name, group in grouped:
    print("\nSchool Code:", name) 
    print(group)

b)grouping and pivot table for the indivdual groups:
grouped1=df.groupby('School')['Age'].agg(['mean','max','min'])
grouped1

c)#18-gruping more the one value to make the group even small
grouped2=df.groupby(['School','Class'])  
for i,j in grouped2:
    print(i)
    print(j)



14. some functions:
df.head(10) 
df.shape
df.columns


df["Name"].str.swapcase() # make lower to upper case and vise versa
df["Name"].str.lower()
df["Name"].str.upper()
#coloum-c1 for display:
df["c1"]
#coloum-c1 and c2 for display:
df[["c1","c3"]]

15. #26-subplot

#plt.subplot(nrows, ncols, index)

plt.subplot(1,4,1)
plt.plot(x, [1, 4, 9, 16])
plt.title("Plot 1")

plt.subplot(1, 4, 2)
plt.plot(x, [2, 3, 5, 7])
plt.title("Plot 2")


16.#Index,columns Customization
r=["Row1", "Row2", "Row3"]
c=["c1", "c2", "c3"]
df = pd.DataFrame(np.random.randn(3,3), index=r,columns=c)


