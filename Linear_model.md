```matlab
x = [160,165,158,172,159,176,160,162,171];
y = [58,63,57,65,62,66,58,59,62];
[w,b] = polyfit(x,y,1);
Predict_y = w(1)*x+w(2);
scatter(x,y);
hold on
plot(x,Predict_y);
```

  

```matlab
w =
    0.4212   -8.2883
```

​    ![untitled](C:\Users\dell\Desktop\untitled.png)

   ![Figure_1](C:\Users\dell\Desktop\Figure_1.png)

```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
from sklearn import linear_model

clf = linear_model.LinearRegression()
x = [160,165,158,172,159,176,160,162,171]
y = [58,63,57,65,62,66,58,59,62]
X = np.array(x).reshape(-1,1)
clf.fit(X,y)
print(clf.coef_) # 
print(clf.intercept_) #
print(clf.score(X,y))
Y = clf.predict(X)
plt.scatter(x,y,color='black')
plt.plot(x,Y,color='blue',linewidth=3)
plt.show()

```



```python
[ 0.42116974]
-8.28830260648
0.730431812357
```

   