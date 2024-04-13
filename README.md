Prac 1 
Aim: Design a simple machine learning model (Linear Regression) g instances and test the same using Python.

import random
from sklearn.linear_model import LinearRegression

feature_set = []
target_set = []

rows = 200
limit = 2000


for i in range(0,rows):

 x = random.randint(0,limit)

 y = random.randint(0,limit)

 z = random.randint(0,limit)

 g = 10*x + 2*y + 3*z

 print("x=",x,"\ty=",y,"\tz=",z,"\tg=",g);

feature_set.append([x,y,z])

target_set.append(g)

model = LinearRegression()

model.fit(feature_set,target_set)

Test_Data = [[1,2,1]]

prediction = model.predict(Test_Data)

print('Prediction:'+str(prediction)+'\t'+ 'Coefficient:'+str(model.coef_))


Prac 2
Aim: For a given set of training data examples stored in a .CSV file implement Logistic Regression algorithm.

import pandas as pd

from sklearn.model_selection import train_test_split

from sklearn.preprocessing import StandardScaler

from sklearn.linear_model import LogisticRegression

from sklearn.metrics import confusion_matrix, accuracy_score

dataset = pd.read_csv("C:/Users/Lokesh/Downloads/diabetes.csv")

print(dataset.head())

x = dataset.iloc[:, [0, 1, 2, 3, 4, 5, 6, 7]].values

y = dataset.iloc[:, [-1]].values

x_train, x_test, y_train, y_test = train_test_split(x, y, test_size=0.2, random_state=100)

sc = StandardScaler()

x_train = sc.fit_transform(x_train)

x_test = sc.transform(x_test)

model = LogisticRegression()

model.fit(x_train, y_train) # Train the model

y_pred = model.predict(x_test)

cm = confusion_matrix(y_test, y_pred)

print("Confusion Matrix :\n ", cm)
print("Accuracy :", accuracy_score(y_test, y_pred) * 100)


Prac 3
Aim: Introduction to R programming

#Creating Variables in R:

var1<-var2<-var3<-"orange"
print(var1)
print(var2)
print(var3)


#R plotting :

plot(c(1,8),c(3,10))


#R Plotting, R Line, Color, Width & Multiline:

l1<-c(1,2,3,4,5,10)

l2<-c(2,5,7,8,9,10)

plot(l1,type="l",col="blue")

lines(l2,type="l",col="red")

#Scatter Plot:


x<-c(5,7,8,7,2,2,9,4,11,12,9,6)

y<-c(99,86,87,88,111,103,87,94,78,75,85,86)

plot(x,y,main="Observation of cars",xlab="car age",ylab="Car Speed")


#Bar charts

x<-c("A","B","C","D")

y<-c(2,4,6,8)

barplot(y,name.arg=x,main="Bar Chart")


#concatenate elements

text1<-"R is"

text2<-"awesome"

cat(text1,text2)


Prac 2B
Aim: Write a program to implement k-Nearest Neighbor algorithm to classify the following data set.

import matplotlib.pyplot as plt

from sklearn.neighbors import KNeighborsClassifier

#Data Set

x = [4, 5, 10, 4, 3, 11, 14 , 8, 10, 12]

y = [21, 19, 24, 17, 16, 25, 24, 22, 21, 21]

classes = [0, 0, 1, 0, 0, 1, 1, 0, 1, 1]

#To plot data set

plt.scatter(x, y, c=classes)

plt.show()

#To merge x and y into single list

data = list(zip(x, y))

print(data)

#model creation

model = KNeighborsClassifier(n_neighbors=1)

# Model is trained

model.fit(data, classes)

new_x = 8

new_y = 21

new_point = [(new_x, new_y)]

prediction = model.predict(new_point)

plt.scatter(x + [new_x], y + [new_y], c=classes + [prediction[0]])

plt.text(x=new_x-1.7, y=new_y-0.7, s=f"new point, class: {prediction[0]}")

plt.show()

model = KNeighborsClassifier(n_neighbors=5)

model.fit(data, classes)

prediction = model.predict(new_point)

print(prediction)
plt.scatter(x + [new_x], y + [new_y], c=classes + [prediction[0]])

plt.text(x=new_x-1.7, y=new_y-0.7, s=f"new point, class: {prediction[0]}")

plt.show()


Prac 3
Aim : Naive Bayes Algorithm


!pip install pgmpy

import pandas as pd

from pgmpy.estimators import MaximumLikelihoodEstimator

from pgmpy.models import BayesianModel

from pgmpy.inference import VariableElimination

data = pd.read_csv("C:/Users/Lokesh/Downloads/ds4.csv")

heart_disease = pd.DataFrame(data)

print(heart_disease)

model = BayesianModel([

 ('age', 'Lifestyle'),

 ('Gender', 'Lifestyle'),

 ('Family', 'heartdisease'),

 ('diet', 'cholestrol'),

 ('Lifestyle', 'diet'),

 ('cholestrol', 'heartdisease'),

 ('diet', 'cholestrol')

])

model.fit(heart_disease, estimator=MaximumLikelihoodEstimator)

HeartDisease_infer = VariableElimination(model)

print('For Age enter SuperSeniorCitizen:0, SeniorCitizen:1, MiddleAged:2, Youth:3, Teen:4')

print('For Gender enter Male:0, Female:1')

print('For Family History enter Yes:1, No:0')

print('For Diet enter High:0, Medium:1')

print('for LifeStyle enter Athlete:0, Active:1, Moderate:2, Sedentary:3')

print('for Cholesterol enter High:0, BorderLine:1, Normal:2')

q = HeartDisease_infer.query(variables=['heartdisease'], 

 evidence={

 'age': int(input('Enter Age: ')),

 'Gender': int(input('Enter Gender: ')),

 'Family': int(input('Enter Family History: ')),

 'diet': int(input('Enter Diet: ')),

 'Lifestyle': int(input('Enter Lifestyle: ')),

 'cholestrol': int(input('Enter Cholestrol: '))

})

print(q)


Prac 4
Aim : K-Means Clustering


import matplotlib.pyplot as plt

from sklearn.cluster import KMeans

x = [4, 5, 10, 4, 3, 11, 14 , 6, 10, 12]

y = [21, 19, 24, 17, 16, 25, 24, 22, 21, 21]

plt.scatter(x, y)

plt.show()

data = list(zip(x, y))

kmeans = KMeans(n_clusters=2)

kmeans.fit(data)

plt.scatter(x, y, c=kmeans.labels_)

plt.show()


Prac 5 
Aim : Data Visualization Using Python


import pandas as pd

import matplotlib.pyplot as plt

# reading the database

data = pd.read_csv("C:/Users/Lokesh/Downloads/tips.csv")

# Scatter plot with day against tip

plt.scatter(data['day'], data['tip'])

# Adding Title to the Plot

plt.title("Scatter Plot")

# Setting the X and Y labels

plt.xlabel('Day')

plt.ylabel('Tip')

plt.show()


Prac 6 
Aim : Pie Diagram, Bar Chart Diagram using Python


import pandas as pd

import matplotlib.pyplot as plt

# reading the database

data = pd.read_csv("C:/Users/Lokesh/Downloads/tips.csv")

# Bar chart with day against tip

plt.bar(data['day'], data['tip'])

plt.title("Bar Chart")

# Setting the X and Y labels

plt.xlabel('Day')

plt.ylabel('Tip')

# Adding the legends

plt.show()

#Pie chart 
import matplotlib.pyplot as plt

import numpy as np

y=np.array([35,25,25,15])

mylabels=["Apples","Bananas","Cherries","Dates"]

plt.pie(y,labels=mylabels)

plt.show()


Prac 7 
Aim : ETL process in Python for Web Scrapping


import requests

from bs4 import BeautifulSoup

def check_word_in_webpage(url, word):

 response = requests.get(url)

 if response.status_code == 200:

 soup = BeautifulSoup(response.content, 'html.parser')

 text_content = soup.get_text()

 if word.lower() in text_content.lower():

 print(f"The word '{word}' is present in the webpage.")

 else:

 print(f"The word '{word}' is not present in the webpage.")

 else:

 print("Failed to retrieve webpage.")

url = input("Enter the url you want to Scrap : ")

word_to_check = input("Enter the text you want to know which is present or not : ")

check_word_in_webpage(url, word_to_check)


Prac 8 
Aim : Data visualization using python libraries


import pandas as pd

import matplotlib. pyplot as plt

#Uploading Dataset

data = pd.read_csv("C:/Users/Lokesh/Downloads/nifty50-index.csv")

print(data)

#Plotting of x-axis & y-axis plot

plt. plot(data['Open '],marker = "o",markeredgecolor="white", markerfacecolor="blue")

plt. plot(data['Close '],marker = "o",markeredgecolor="white", markerfacecolor="orange")

plt.grid()

plt. title("Line Plot of NIFTY-50 by using Matplotlib")

plt. xlabel('Open')

plt. ylabel('Close')

plt.legend(['Open', 'Close'])

plt. show()

#DATA VISUALIZATION USING SEABORN

import pandas as pd

import seaborn as sns

import matplotlib.pyplot as plt

# Load dataset

data = pd.read_csv("C:/Users/Lokesh/Downloads/nifty50-index.csv")

print("Himanshu Singh KFMSCIT010")

# Plotting

plt.figure(figsize=(10, 6))

sns.lineplot(data=data[['Open', 'Close']], markers=True, marker='o', 

markeredgecolor="white", palette=['green', 'red'])

plt.title("Line Plot of NIFTY-50 by using Seaborn")

plt.xlabel('Index')

plt.ylabel('Price')

plt.grid(True)

plt.show()


#DATA VISUALIZATION USING PLOTLY

import pandas as pd

import plotly.express as px

# Load dataset

data = pd.read_csv("C:/Users/Lokesh/Downloads/nifty50-index.csv")

print("Himanshu Singh KFMSCIT010")

# Plotting

fig = px.line(data, x=data.index, y=['Open', 'Close'], markers=True,

 title="( Himanshu Singh KFMSCIT010)Line Plot of NIFTY-50 using Plotly", 

labels={'index': 'Index', 'value': 'Price'},

 color_discrete_sequence=['green', 'red'])

fig.update_layout(legend_title='Price', legend=dict(x=0, y=1, traceorder='normal'),

 plot_bgcolor='rgba(0,0,0,0)')

fig.show()


Prac 9
Aim : Decision Tree Classifier

import numpy as np

import pandas as pd # Import Pandas for data loading

import matplotlib.pyplot as plt

from sklearn.tree import DecisionTreeClassifier, plot_tree

from sklearn.model_selection import train_test_split

from sklearn.metrics import accuracy_score

data = pd.read_csv(' C:/Users/Lokesh/Downloads/iris.csv')

print(data.head())

# Assuming the target variable is in a column named 'target'

X = data.drop('species', axis=1)

y = data['species']

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

model = DecisionTreeClassifier()

model.fit(X_train, y_train)

y_pred = model.predict(X_test)

accuracy = accuracy_score(y_test, y_pred)

print(f"Accuracy: {accuracy:.2f}")

# Visualize and interpret the generated decision tree

plt.figure(figsize=(12, 8))

plot_tree(model, filled=True, feature_names=X.columns, 

class_names=y.unique().astype(str))

plt.title("Decision Tree Visualization")

plt.show()


