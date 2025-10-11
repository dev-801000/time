# time

# Artificial Intelligence & Machine Learning Practicals

## PRACTICAL NO: 1(A)
### **AIM**
Breadth First Search (BFS) Algorithm Implementation

### 🅐 BFS Shortest Path Algorithm

**Algorithm:** Implements BFS to find the shortest path between two nodes in a graph using queue-based traversal.

```python
class first:
    def __init__(self, graph, start, goal):
        self.start = start
        self.goal = goal
        self.graph = graph
    
    def bfs_shortest_path(self):
        explored = []
        queue = [[self.start]]
        
        if self.start == self.goal:
            return "That was easy! Start = goal"
        
        while queue:
            path = queue.pop(0)
            node = path[-1]
            neighbours = self.graph[node]
            
            for neighbour in neighbours:
                new_path = list(path)
                new_path.append(neighbour)
                queue.append(new_path)
                
                if neighbour == self.goal:
                    return new_path
            
            explored.append(node)
        
        return "So sorry, but a connecting path doesn't exist :("

# Romania Graph Representation
graph = {
    'Arad': ['Zerind', 'Sibiu', 'Timisoara'],
    'Bucharest': ['Urziceni','Pitesti', 'Giurgiu','Fagaras'],
    'Craiova': ['Dobreta', 'Rimnicu Vilcea', 'Pitesti'],
    'Dobreta': ['Mehadia'],
    'Eforie': ['Hirsova'],
    'Iasai': ['Vaslui','Neamt'],
    'Lugoj': ['Timisoara','Mehadia'],
    'Oradea': ['Zerind','Sibiu'],
    'Pitesti': ['Rimnicu Vilcea'],
    'Urziceni': ['Vaslui'],
    'Zerind': ['Oradea','Arad'],
    'Sibiu': ['Oradea','Arad','Rimnicu Vilcea','Fagaras'],
    'Timisoara': ['Arad','Lugoj'],
    'Mehadia': ['Lugoj','Dobreta'],
    'Rimnicu Vilcea': ['Sibiu','Pitesti','Craiova'],
    'Fagaras': ['Sibiu','Bucharest'],
    'Giurgiu': ['Bucharest'],
    'Vaslui': ['Urziceni','Iasai'],
    'Neamt': ['Iasai']
}

# Execute BFS
f = first(graph, 'Arad', 'Bucharest')
print(f.bfs_shortest_path())
```

**Output:** Returns the shortest path from Arad to Bucharest

---

## PRACTICAL NO: 1(B)
### **AIM**
Iterative Deepening Depth-First Search (IDDFS) Algorithm

### 🅑 IDDFS Implementation

**Algorithm:** Combines benefits of DFS and BFS by iteratively increasing depth limit until goal is found.

```python
# Same graph as above
graph = {
    'Arad': ['Zerind', 'Sibiu', 'Timisoara'],
    'Bucharest': ['Urziceni','Pitesti', 'Giurgiu','Fagaras'],
    'Craiova': ['Dobreta', 'Rimnicu Vilcea', 'Pitesti'],
    'Dobreta': ['Mehadia'],
    'Eforie': ['Hirsova'],
    'Iasai': ['Vaslui','Neamt'],
    'Lugoj': ['Timisoara','Mehadia'],
    'Oradea': ['Zerind','Sibiu'],
    'Pitesti': ['Rimnicu Vilcea'],
    'Urziceni': ['Vaslui'],
    'Zerind': ['Oradea','Arad'],
    'Sibiu': ['Oradea','Arad','Rimnicu Vilcea','Fagaras'],
    'Timisoara': ['Arad','Lugoj'],
    'Mehadia': ['Lugoj','Dobreta'],
    'Rimnicu Vilcea': ['Sibiu','Pitesti','Craiova'],
    'Fagaras': ['Sibiu','Bucharest'],
    'Giurgiu': ['Bucharest'],
    'Vaslui': ['Urziceni','Iasai'],
    'Neamt': ['Iasai']
}

def IDDFS(root, goal):
    depth = 0
    while True:
        print("Looping at depth %i " % (depth))
        result = DLS(root, goal, depth)
        print("Result: %s, Goal: %s" % (result, goal))
        if result == goal:
            return result
        depth = depth + 1

def DLS(node, goal, depth):
    print("node: %s, goal %s, depth: %i" % (node, goal, depth))
    if depth == 0 and node == goal:
        print(" --- Found goal, returning --- ")
        return node
    elif depth > 0:
        print("Looping through children: %s" % (graph.get(node, [])))
        for child in graph.get(node, []):
            if goal == DLS(child, goal, depth-1):
                return goal

# Execute IDDFS
IDDFS('Arad', 'Bucharest')
```

**Output:** Shows iterative deepening process with depth-limited search at each level

---

## PRACTICAL NO: 2(A)
### **AIM**
A* Search Algorithm Implementation

### 🅐 A* Search with Heuristic

**Algorithm:** Uses both actual cost (g) and heuristic cost (h) to find optimal path: f(n) = g(n) + h(n)

```python
# Graph representation
graph = {
    'Arad': ['Zerind', 'Timisoara', 'Sibiu'],
    'Bucharest': ['Urziceni','Pitesti', 'Giurgiu','Fagaras'],
    'Craiova': ['Dobreta', 'Rimnicu Vilcea', 'Pitesti'],
    'Dobreta': ['Mehadia'],
    'Eforie': ['Hirsova'],
    'Iasai': ['Vaslui','Neamt'],
    'Lugoj': ['Timisoara','Mehadia'],
    'Oradea': ['Zerind','Sibiu'],
    'Pitesti': ['Rimnicu Vilcea','Bucharest','Craiova'],
    'Urziceni': ['Vaslui'],
    'Zerind': ['Oradea','Arad'],
    'Sibiu': ['Oradea','Arad','Rimnicu Vilcea','Fagaras'],
    'Timisoara': ['Arad','Lugoj'],
    'Mehadia': ['Lugoj','Dobreta'],
    'Rimnicu Vilcea': ['Sibiu','Pitesti','Craiova'],
    'Fagaras': ['Sibiu','Bucharest'],
    'Giurgiu': ['Bucharest'],
    'Vaslui': ['Urziceni','Iasai'],
    'Neamt': ['Iasai']
}

# Path costs between cities
pc = {
    ('Arad','Zerind'): 75,
    ('Arad','Timisoara'): 118,
    ('Arad','Sibiu'): 140,
    ('Zerind','Oradea'): 71,
    ('Zerind','Arad'): 75,
    ('Timisoara','Arad'): 118,
    ('Timisoara','Lugoj'): 111,
    ('Sibiu','Arad'): 140,
    ('Sibiu','Rimnicu Vilcea'): 80,
    ('Sibiu','Fagaras'): 99,
    ('Sibiu','Oradea'): 151,
    ('Oradea','Zerind'): 71,
    ('Oradea','Sibiu'): 151,
    ('Lugoj','Timisoara'): 111,
    ('Lugoj','Mehadia'): 70,
    ('Rimnicu Vilcea','Sibiu'): 80,
    ('Rimnicu Vilcea','Pitesti'): 97,
    ('Rimnicu Vilcea','Craiova'): 146,
    ('Fagaras','Sibiu'): 99,
    ('Fagaras','Bucharest'): 211,
    ('Mehadia','Lugoj'): 70,
    ('Mehadia','Dobreta'): 75,
    ('Pitesti','Rimnicu Vilcea'): 97,
    ('Pitesti','Bucharest'): 101,
    ('Pitesti','Craiova'): 138,
    ('Craiova','Rimnicu Vilcea'): 146,
    ('Craiova','Dobreta'): 120,
    ('Craiova','Pitesti'): 138,
    ('Bucharest','Fagaras'): 211,
    ('Bucharest','Bucharest'): 0,
    ('Bucharest','Pitesti'): 101,
    ('Bucharest','Giurgiu'): 90,
    ('Bucharest','Urziceni'): 85,
}

# Straight-line distances to Bucharest (heuristic)
locs = {
    'Arad': 366,
    'Bucharest': 0,
    'Craiova': 160,
    'Dobreta': 242,
    'Eforie': 161,
    'Iasai': 226,
    'Lugoj': 244,
    'Oradea': 380,
    'Pitesti': 100,
    'Urziceni': 80,
    'Zerind': 374,
    'Sibiu': 253,
    'Timisoara': 329,
    'Mehadia': 241,
    'Rimnicu Vilcea': 193,
    'Fagaras': 176,
    'Giurgiu': 77,
    'Vaslui': 199,
    'Neamt': 234
}

def DFS(g, v, goal, explored, path_so_far, m):
    """Returns path from v to goal in g using A* heuristic"""
    explored.add(v)
    node = []
    
    if v == goal:
        return path_so_far + "->" + v
    
    for w in g[v]:
        if w not in explored:
            f = locs.get(w) + pc.get((v, w))  # f(n) = h(n) + g(n)
            if m > f:
                m = f
                print("%i%s%s" % (m, v, w))
                node = w
    
    p = DFS(g, node, goal, explored, path_so_far + "->" + v, m)
    if p:
        return p
    return ""

print(DFS(graph, 'Arad', 'Bucharest', set(), "", 1000))
```

**Output:** Shows optimal path from Arad to Bucharest using A* algorithm

---

## PRACTICAL NO: 2(B)
### **AIM**
Best-First Search with Modified Heuristic

### 🅑 Best-First Search Implementation

**Algorithm:** Greedy search that always expands the node closest to the goal based on heuristic function.

```python
# Same graph structure as A*
graph = {
    'Arad': ['Zerind', 'Timisoara', 'Sibiu'],
    'Bucharest': ['Urziceni','Pitesti', 'Giurgiu','Fagaras'],
    'Craiova': ['Dobreta', 'Rimnicu Vilcea', 'Pitesti'],
    'Dobreta': ['Mehadia'],
    'Eforie': ['Hirsova'],
    'Iasai': ['Vaslui','Neamt'],
    'Lugoj': ['Timisoara','Mehadia'],
    'Oradea': ['Zerind','Sibiu'],
    'Pitesti': ['Rimnicu Vilcea','Bucharest','Craiova'],
    'Urziceni': ['Vaslui'],
    'Zerind': ['Oradea','Arad'],
    'Sibiu': ['Oradea','Arad','Rimnicu Vilcea','Fagaras'],
    'Timisoara': ['Arad','Lugoj'],
    'Mehadia': ['Lugoj','Dobreta'],
    'Rimnicu Vilcea': ['Sibiu','Pitesti','Craiova'],
    'Fagaras': ['Sibiu','Bucharest'],
    'Giurgiu': ['Bucharest'],
    'Vaslui': ['Urziceni','Iasai'],    
    'Neamt': ['Iasai']
}

# Modified path costs
pc = {
    ('Arad','Arad'): 0,
    ('Arad','Zerind'): 75,
    ('Arad','Timisoara'): 118,
    ('Arad','Sibiu'): 140,
    ('Zerind','Oradea'): 146,
    ('Zerind','Arad'): 75,
    ('Timisoara','Arad'): 118,
    ('Timisoara','Lugoj'): 229,
    ('Sibiu','Arad'): 140,
    ('Sibiu','Rimnicu Vilcea'): 220,
    ('Sibiu','Fagaras'): 239,
    ('Sibiu','Oradea'): 297,
    ('Oradea','Zerind'): 362,
    ('Oradea','Sibiu'): 297,
    ('Lugoj','Mehadia'): 361,
    ('Rimnicu Vilcea','Pitesti'): 317,
    ('Rimnicu Vilcea','Craiova'): 366,
    ('Rimnicu Vilcea','Sibiu'): 494,
    ('Fagaras','Bucharest'): 450,
    ('Fagaras','Sibiu'): 798,
    ('Mehadia','Dobreta'): 436,
    ('Pitesti','Bucharest'): 418,
    ('Pitesti','Craiova'): 455,
    ('Pitesti','Rimnicu Vilcea'): 791,
    ('Craiova','Rimnicu Vilcea'): 146,
    ('Craiova','Dobreta'): 120,
    ('Craiova','Pitesti'): 138,
    ('Bucharest','Fagaras'): 211,
    ('Bucharest','Bucharest'): 0,
    ('Bucharest','Pitesti'): 101,
    ('Bucharest','Giurgiu'): 90,
    ('Bucharest','Urziceni'): 85,
}

# Heuristic values
locs = {
    'Arad': 366, 'Bucharest': 0, 'Craiova': 160, 'Dobreta': 242,
    'Eforie': 161, 'Iasai': 226, 'Lugoj': 244, 'Oradea': 380,
    'Pitesti': 100, 'Urziceni': 80, 'Zerind': 374, 'Sibiu': 253,
    'Timisoara': 329, 'Mehadia': 241, 'Rimnicu Vilcea': 193,
    'Fagaras': 176, 'Giurgiu': 77, 'Vaslui': 199, 'Neamt': 234
}

# Search function values
sf = {
    'Arad': 366, 'Bucharest': 450, 'Craiova': 526, 'Dobreta': 242,
    'Eforie': 161, 'Iasai': 226, 'Lugoj': 244, 'Oradea': 671,
    'Pitesti': 417, 'Urziceni': 80, 'Zerind': 449, 'Sibiu': 393,
    'Timisoara': 447, 'Mehadia': 241, 'Rimnicu Vilcea': 413,
    'Fagaras': 415, 'Giurgiu': 77, 'Vaslui': 199, 'Neamt': 234
}

def DFS(g, v, goal, explored, path_so_far, alt1):
    explored.add(v)
    m = 1000
    node = []
    fcost = set()
    
    if v == goal:
        return path_so_far + "->" + v
    
    for w in g[v]:
        if w == goal:
            return path_so_far + "->" + w
        f = locs.get(w) + pc.get((v, w))
        sf[v] = max(sf.get(v), f)
        print("%s:%i,%i" % (w, sf[w], f))
        fcost.add(sf.get(w))
        if m > f:
            m = f
            print("%i%s%s" % (m, v, w))
            node = w
    
    for k, x in g.items():
        if v in x:
            pnt = k
    
    if v != 'Arad':
        fcost = set()
        for s in g[pnt]:
            fcost.add(sf.get(s))
        alt = sorted(fcost)[1]
        print(alt, alt1)
        bestf = min(m, alt1)
        print(list(sf.keys())[list(sf.values()).index(bestf)])
        best = list(sf.keys())[list(sf.values()).index(bestf)]
        
        p = DFS(g, best, goal, explored, path_so_far + "->" + v, alt)
        if p:
            return p
    return ""

print(DFS(graph, 'Arad', 'Bucharest', set(), "", 1000))
```

**Output:** Shows best-first search path with backtracking when needed

---

## PRACTICAL NO: 3
### **AIM**
Decision Tree Implementation with R

### 🅒 Decision Tree with rpart

**Algorithm:** Create decision tree for restaurant waiting prediction using R's rpart package.

```r
install.packages("rpart")
install.packages("rpart.plot")

library(rpart)
library(rpart.plot)


# find a location
getwd()
#"C:/Users/Abhikesh/Documents" getwd type kar nar ne ke bad aaye ga
setwd("C:/Users/Abhikesh/Documents")
getwd()

#-----

data <- data.frame(
  ALTERNATE = c("Yes","No","Yes","No","Yes"),
  BAR = c("No","Yes","No","Yes","Yes"),
  FRIDAY = c("Yes","No","Yes","Yes","No"),
  HUNGRY = c("Yes","No","Yes","Yes","No"),
  PRICE = c("$$","$","$$$","$$","$"),
  RAINING = c("No","Yes","No","No","Yes"),
  RESERVATION = c("Yes","No","Yes","No","No"),
  TYPE = c("French","Italian","Thai","Burger","Italian"),
  WAIT_ESTIMATE = c("0-10","30-60","10-30",">60","0-10"),
  WILLWAIT = c("Yes","No","Yes","No","Yes")
)
write.csv(data, "restaurant.csv", row.names = FALSE)

#-------------

library(rpart)
library(rpart.plot)

d <- read.csv("restaurant.csv")

mytree <- rpart(WILLWAIT ~ ., data = d, minsplit = 1, minbucket = 1)

rpart.plot(mytree)

p <- predict(mytree)
print(p)




```

**Dataset Structure (restaurant.csv):**
- **WILLWAIT**: Target variable (Yes/No)
- **Features**: ALT, BAR, FRI, HUN, PAT, PRICE, RAIN, RES, TYPE, EST

**Output:** Visual decision tree showing decision rules for restaurant waiting

---

## PRACTICAL NO: 4
### **AIM**
Neural Network Implementation in R

### 🅓 Neural Network with neuralnet

**Algorithm:** Create neural network for restaurant dataset using R's neuralnet package.

```
getwd()
a <- read.csv(file.choose())
head(a)
View(a)

install.packages("ggplot2")
library(ggplot2)


ggplot(a, aes(x = TYPE, fill = WILLWAIT)) +
  geom_bar(position = "dodge") +
  labs(title = "Restaurant Type vs Will Wait",
       x = "Restaurant Type",
       y = "Count") +
  theme_minimal()


```

**Network Configuration:**
- **Input Layer**: 10 features (ALT, BAR, FRI, HUN, PAT, PRICE, RAIN, RES, TYPE, EST)
- **Hidden Layer**: 3 neurons
- **Output Layer**: 1 neuron (WILLWAIT)

**Output:** Neural network diagram showing weights and connections

---

## PRACTICAL NO: 6
### **AIM**
AdaBoost Algorithm Implementation

### 🅔 AdaBoost Ensemble Classifier

**Algorithm:** Implement AdaBoost to create ensemble of weak classifiers and compare with individual classifiers.

```python
from sklearn.ensemble import AdaBoostClassifier
from sklearn import datasets
from sklearn.model_selection import train_test_split
from sklearn import metrics

# Load Iris dataset
iris = datasets.load_iris()
X = iris.data
y = iris.target

# Split dataset
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3)  # 70% training and 30% test

# Create AdaBoost classifier
abc = AdaBoostClassifier(n_estimators=50, learning_rate=1)
print(abc)

# Train the model
model = abc.fit(X_train, y_train)
print(model)

# Make predictions
y_pred = model.predict(X_test)
print(model)

# Evaluate performance
print("Accuracy:", metrics.accuracy_score(y_test, y_pred))
```

**Key Parameters:**
- **n_estimators**: 50 (number of weak learners)
- **learning_rate**: 1.0 (weight applied to each classifier)
- **Dataset**: Iris (4 features, 3 classes)

**Output:** Shows AdaBoost classifier configuration and accuracy score

---

## PRACTICAL NO: 7
### **AIM**
Naive Bayes Learning Implementation

### 🅕 Naive Bayes Classifier in R

**Algorithm:** Implement Naive Bayes classifier for restaurant dataset using conditional probability.

```r
# Load required library
library(e1071)

# Read training and test datasets
Train <- read.csv(file.choose())  # Select training file
Test <- read.csv(file.choose())   # Select test file

# Create Naive Bayes model
model <- naiveBayes(WILLWAIT ~ ., data = Train)

# Check model class
class(model)
# [1] "naiveBayes"

# Display model details
model
```

**Model Output:**
```
Naive Bayes Classifier for Discrete Predictors

Call:
naiveBayes.default(x = X, y = Y, laplace = laplace)

A-priori probabilities:
Y
 No Yes 
0.5 0.5 

Conditional probabilities:
       ALT
Y        No  Yes
  No  0.5  0.5
  Yes 0.5  0.5

       BAR
Y        No  Yes
  No  0.5  0.5
  Yes 0.5  0.5

       FRI
Y             No        Yes
  No  0.5000000 0.5000000
  Yes 0.6666667 0.3333333

       HUN
Y             No        Yes
  No  0.6666667 0.3333333
  Yes 0.1666667 0.8333333

       PAT
Y       Full None      Some
  No  0.6666667 0.3333333 0.0000000
  Yes 0.3333333 0.0000000 0.6666667

       PRICE
Y         $   $$     $$$
  No  0.6666667 0.0000000 0.3333333
  Yes 0.5000000 0.3333333 0.1666667

       RAIN
Y        No  Yes
  No  0.6666667 0.3333333
  Yes 0.6666667 0.3333333

       RES
Y        No  Yes
  No  0.6666667 0.3333333
  Yes 0.5000000 0.5000000

       TYPE
Y       Burger    French   Italian      Thai
  No  0.3333333 0.1666667 0.1666667 0.3333333
  Yes 0.3333333 0.1666667 0.1666667 0.3333333

       EST
Y         >60     0-10    30-60   30-Oct
  No  0.3333333 0.3333333 0.1666667 0.1666667
  Yes 0.0000000 0.6666667 0.1666667 0.1666667
```

**Make Predictions:**
```r
# Predict on test set
pred <- predict(model, Test)

# Display prediction results
table(pred)
# pred
#  No Yes 
#   8   4
```

**Output:** Shows conditional probabilities for each feature and class predictions

---

## PRACTICAL NO: 8
### **AIM**
K-Nearest Neighbors (K-NN) Algorithm

### 🅖 K-NN Classification

**Algorithm:** Implement K-NN classifier to classify new data points based on k nearest neighbors.

```python
import matplotlib.pyplot as plt
from sklearn.neighbors import KNeighborsClassifier

# Training data
x = [4, 5, 10, 4, 3, 11, 14, 8, 10, 12]
y = [21, 19, 24, 17, 16, 25, 24, 22, 21, 21]
classes = [0, 0, 1, 0, 0, 1, 1, 0, 1, 1]

# Plot training data
plt.scatter(x, y, c=classes)
plt.show()

# Prepare data for sklearn
data = list(zip(x, y))

# Create KNN classifier
knn = KNeighborsClassifier(n_neighbors=1)
knn.fit(data, classes)

# New point to classify
new_x = 8
new_y = 21
new_point = [(new_x, new_y)]

# Make prediction
prediction = knn.predict(new_point)

# Plot results with new point
plt.scatter(x + [new_x], y + [new_y], c=classes + [prediction[0]])
plt.text(x=new_x-1.7, y=new_y-0.7, s=f"new point, class: {prediction[0]}")
plt.show()
```

**Algorithm Steps:**
1. Store all training data points
2. For new point, calculate distance to all training points
3. Find k nearest neighbors
4. Assign class based on majority vote of k neighbors
5. With k=1, assign class of single nearest neighbor

**Output:** Scatter plot showing classification of new point based on nearest neighbor

---

## PRACTICAL NO: 9
### **AIM**
Association Rule Mining & Data Clustering

### 🅗 Data Clustering with Support Vector Machines

**Algorithm:** Generate sample data and demonstrate clustering/classification boundaries using SVM concepts.

```python
from sklearn.datasets import make_blobs
import matplotlib.pyplot as plt
import numpy as np

# Generate sample data with 2 clusters
X, Y = make_blobs(n_samples=500, centers=2, random_state=0, cluster_std=0.40)

# Plot initial scatter
plt.scatter(X[:, 0], X[:, 1], c=Y, s=50, cmap='spring')
plt.show()

# Create line fitting data
xfit = np.linspace(-1, 3.5)

# Plot scatter with decision boundaries
plt.scatter(X[:, 0], X[:, 1], c=Y, s=50, cmap='spring')

# Plot multiple potential decision boundaries
for m, b, d in [(1, 0.65, 0.33), (0.5, 1.6, 0.55), (-0.2, 2.9, 0.2)]:
    yfit = m * xfit + b
    plt.plot(xfit, yfit, '-k')
    plt.fill_between(xfit, yfit - d, yfit + d, edgecolor='none', 
                     color='#AAAAAA', alpha=0.4)

plt.xlim(-1, 3.5)
plt.show()

# Display data
print("X (Features):", X)
print("Y (Labels):", Y)
```

**Key Concepts:**
- **make_blobs**: Creates Gaussian blob clusters for classification
- **Decision Boundaries**: Lines separating different classes
- **Margin**: Distance between decision boundary and nearest data points
- **Support Vectors**: Data points closest to decision boundary

**Output:** 
1. Scatter plot of two-class data
2. Multiple decision boundaries with margins
3. Feature matrix X and label vector Y

---

## 📊 Dataset Requirements

### Restaurant Dataset (restaurant.csv)
Required columns for Decision Tree and Neural Network practicals:
- **WILLWAIT**: Target variable (Yes/No)
- **ALT**: Alternative available (Yes/No)
- **BAR**: Bar available (Yes/No) 
- **FRI**: Friday (Yes/No)
- **HUN**: Hungry (Yes/No)
- **PAT**: Patrons (None/Some/Full)
- **PRICE**: Price range ($/$$/$$)
- **RAIN**: Raining (Yes/No)
- **RES**: Reservation (Yes/No)
- **TYPE**: Food type (French/Italian/Thai/Burger)
- **EST**: Estimated wait (0-10/10-30/30-60/>60)

---

## 🛠️ Required Libraries

### Python Libraries:
```bash
pip install scikit-learn matplotlib numpy
```

### R Packages:
```r
install.packages(c("rpart", "rpart.plot", "neuralnet", "e1071"))
```

---

## 🚀 Getting Started

1. **Set up Environment**: Install Python/R and required libraries
2. **Prepare Datasets**: Create or download restaurant.csv file
3. **Run Algorithms**: Execute each practical step by step
4. **Analyze Results**: Compare different algorithm performances
5. **Experiment**: Try different parameters and datasets

---

## 📝 Key Learning Outcomes

- **Search Algorithms**: BFS, DFS, A*, Best-First Search
- **Machine Learning**: Decision Trees, Neural Networks, Naive Bayes
- **Ensemble Methods**: AdaBoost for combining weak learners
- **Classification**: K-NN, SVM concepts
- **Clustering**: Data separation and boundary identification
- **Evaluation**: Accuracy metrics and model comparison

---

*Happy Learning! 🤖📊*
