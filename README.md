PYTHON PROJECT AXIA

This project is designed to demonstrate my Python data analysis skills
using the Pandas and Matplotlib libraries. I'll be working with raw
sales data , My  task is to clean it, explore it, and extract useful
business insights. The goal is to simulate the day-to-day
responsibilities of a data analyst: transforming messy data into clear,
actionable findings using Python.


```python
#IMPORTING THE REQUIRED LIBRARIES

import pandas as pd
import matplotlib.pyplot as plt 
```


```python
#GETTING THE DATA INTO PYTON TO BE STORED AS A DATAFRAME 
data = pd.read_csv("C:\\Users\\User\\Documents\\raw.csv" , index_col = 0, header = 1)

```


```python
#GETTING A CLEARER VIEW OF THE DATASET

print(data.columns)

```

    Index(['Order ID', 'Date', 'Product', 'Price', 'Quantity', 'Purchase Type',
           'Payment Method', 'Manager', 'City'],
          dtype='object')
    


```python

data.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Order ID</th>
      <th>Date</th>
      <th>Product</th>
      <th>Price</th>
      <th>Quantity</th>
      <th>Purchase Type</th>
      <th>Payment Method</th>
      <th>Manager</th>
      <th>City</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>NaN</th>
      <td>10452</td>
      <td>7/11/2022</td>
      <td>Fries</td>
      <td>3.49</td>
      <td>573.07</td>
      <td>Online</td>
      <td>Gift Card</td>
      <td>Tom      Jackson</td>
      <td>London</td>
    </tr>
    <tr>
      <th>NaN</th>
      <td>10453</td>
      <td>7/11/2022</td>
      <td>Beverages</td>
      <td>2.95</td>
      <td>745.76</td>
      <td>Online</td>
      <td>Gift Card</td>
      <td>Pablo Perez</td>
      <td>Madrid</td>
    </tr>
    <tr>
      <th>NaN</th>
      <td>10454</td>
      <td>7/11/2022</td>
      <td>Sides &amp; Other</td>
      <td>4.99</td>
      <td>200.40</td>
      <td>In-store</td>
      <td>Gift Card</td>
      <td>Joao    Silva</td>
      <td>Lisbon</td>
    </tr>
    <tr>
      <th>NaN</th>
      <td>10455</td>
      <td>8/11/2022</td>
      <td>Burgers</td>
      <td>12.99</td>
      <td>569.67</td>
      <td>In-store</td>
      <td>Credit Card</td>
      <td>Walter Muller</td>
      <td>Berlin</td>
    </tr>
    <tr>
      <th>NaN</th>
      <td>10456</td>
      <td>8/11/2022</td>
      <td>Chicken Sandwiches</td>
      <td>9.95</td>
      <td>201.01</td>
      <td>In-store</td>
      <td>Credit Card</td>
      <td>Walter Muller</td>
      <td>Berlin</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.shape
```




    (254, 9)




```python
data.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Float64Index: 254 entries, nan to nan
    Data columns (total 9 columns):
     #   Column          Non-Null Count  Dtype  
    ---  ------          --------------  -----  
     0   Order ID        254 non-null    int64  
     1   Date            254 non-null    object 
     2   Product         254 non-null    object 
     3   Price           254 non-null    float64
     4   Quantity        254 non-null    float64
     5   Purchase Type   254 non-null    object 
     6   Payment Method  254 non-null    object 
     7   Manager         254 non-null    object 
     8   City            254 non-null    object 
    dtypes: float64(2), int64(1), object(6)
    memory usage: 19.8+ KB
    


```python
data.dtypes
```




    Order ID            int64
    Date               object
    Product            object
    Price             float64
    Quantity          float64
    Purchase Type      object
    Payment Method     object
    Manager            object
    City               object
    dtype: object




```python
data.isnull().sum()
```




    Order ID          0
    Date              0
    Product           0
    Price             0
    Quantity          0
    Purchase Type     0
    Payment Method    0
    Manager           0
    City              0
    dtype: int64



THE DESCRIPTIVE STATICTICS OF OUR DATASET 

THE TOTAL ROWS IS 254 AND THE COLUMNS ARE 9



```python
#DESCRIPTIVE STATISTICS OF THE DATASET
data.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Order ID</th>
      <th>Price</th>
      <th>Quantity</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>254.000000</td>
      <td>254.000000</td>
      <td>254.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>10584.133858</td>
      <td>7.102323</td>
      <td>460.611457</td>
    </tr>
    <tr>
      <th>std</th>
      <td>75.889181</td>
      <td>4.341855</td>
      <td>214.888699</td>
    </tr>
    <tr>
      <th>min</th>
      <td>10452.000000</td>
      <td>2.950000</td>
      <td>200.400000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>10520.250000</td>
      <td>3.490000</td>
      <td>201.010000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>10583.500000</td>
      <td>4.990000</td>
      <td>538.880000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>10649.750000</td>
      <td>9.950000</td>
      <td>677.440000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>10713.000000</td>
      <td>29.050000</td>
      <td>754.430000</td>
    </tr>
  </tbody>
</table>
</div>



QUESTION 1 

THE MOST PREFFERED METHOD OF PAYMENT IS CREDIT CARD WITH A STAGERRING NUMBER OF 120, FOLLOWED BY PAYMENT BY CASH(76), GIFTCARDS(58)


```python
#THE MOST PREFERRED METHOD OF PAYMENT
#using counter to implement this operation
from collections import Counter
counts =Counter(data["Payment Method"])
most_preffered = counts.most_common(1)[0]

print ("the most preffered form of payment is " ,  most_preffered)
```

    the most preffered form of payment is  (' Credit Card', 120)
    

QUESTION 2

#THE MOST SELLLING PRODUCT BY QUANTITY 


version A


```python
#MOST SELLING PRODUCT BY QUANTITY ()
top_by_quantityA = data.query("Quantity == Quantity.max()")["Product"].values[0]
print("The top selling product by quantity is", top_by_quantityA)
```

    The top selling product by quantity is Burgers
    

VERSION B


```python
top_by_quantityB = data.nlargest(1, "Quantity")["Product"].values[0]
print("The top selling product by quantity is", top_by_quantityB)
```

    The top selling product by quantity is Burgers
    

THUS THE MOST SELLING PRODUCTS BY QUANTITY ARE THE BEVERAGES 

#THE MOST SELLING PRODUCT BY REVENUE  


#VERSION A


```python
#Creating the revenue column 
data["Revenue"] = data["Quantity"] * data["Price"]
```


```python
top_by_revenueA= data.query("Revenue == Revenue.max()")["Product"].values[0]
print("The top selling product by revenue generated is", top_by_revenueA)
```

    The top selling product by revenue generated is Fries
    

#VERSION B


```python
top_by_revenueB = data.nlargest(1, "Revenue")["Product"].values[0]
print("The top selling product by revenue generated is", top_by_revenueB)
```

    The top selling product by revenue generated is Fries
    

THUS THE MOST SELLING PRODUCT BY REVENUE IS FRIES 

QUESTION 3
Which City had maximum revenue, and Which Manager earned maximum REVENUE?


```python
city_max_rev = data.nlargest(1, "Revenue")["City"].values[0]
manager_max_rev = data.query("Revenue == Revenue.max()")["Manager"].values[0]
print("the city with the maximum revenue is ", city_max_rev)
print("the manager with the maximum revenue generated is ", manager_max_rev)
```

    the city with the maximum revenue is  Lisbon
    the manager with the maximum revenue generated is  Joao Silva
    

the city with the maximum revenue is  Lisbon
and the  manager with the maximum revenue generated is  Joao Silva

QUESTION 4
What was the Average revenue?


```python
avrg_revenue = data["Revenue"].mean()
print("the average revenue generated is", avrg_revenue)
```

    the average revenue generated is 3029.5899968503945
    

QUESTION 5
What was the Average Revenue of November & December?


```python
#converting the date to a more standardzed format to be able to subset the month 
data["Date"] = pd.to_datetime(data["Date"])
nov_date = data[(data["Date"].dt.month == 11)]
dec_date = data[(data["Date"].dt.month ==12 )]
nov_avrg_revenue = nov_date["Revenue"].mean()
dec_avrg_revenue = dec_date["Revenue"].mean()
print("the average revenue of the month November is ", nov_avrg_revenue)
print("And the average revenue for the month of December is", dec_avrg_revenue)

```

    the average revenue of the month November is  2970.2529525773207
    And the average revenue for the month of December is 3195.7490085106406
    

QUESTION 6 
What was the Standard Deviation of Revenue and Quantity?


```python
std_rev = data["Revenue"].std()
std_quan = data["Quantity"].std()
print("The standard deviation of the revenue is ", std_rev)
print("And the standard deiation of the Quantity is ", std_quan)
```

    The standard deviation of the revenue is  2420.11837804107
    And the standard deiation of the Quantity is  214.88869921528863
    

QUESTION 7 
What was the Variance of Revenue and Quantity?


```python
variance_rev = data["Revenue"].var()
variance_quan = data["Quantity"].var()
print("The variance of the revenue generated is ", variance_rev)
print("Ans also, the variance of the quantity is ", variance_quan)
```

    The variance of the revenue generated is  5856972.963732139
    Ans also, the variance of the quantity is  46177.15305043879
    

QUESTION 8
Was the revenue increasing or decreasing over the time?


```python
#USING A LINE CHART TO GET AN OVERVIEW OF THE TREND OF THE REVENUE USING A 7 DAYS ROLLING AVERAGE 
data["revenue_mv7"] = data["Revenue"].rolling(window=7).mean()
plt.figure(figsize=(20,20))
plt.plot(data["Date"], data["Revenue"], marker ="o", alpha=0.5, label = "Daily revenue")
plt.plot(data["Date"], data["revenue_mv7"], color = "red" , label = "7-days moving Average")
plt.grid(True)
plt.title("REVENUE TREND OVER TIME")
plt.xlabel("DATE")
plt.ylabel("REVENUE")
```




    Text(0, 0.5, 'REVENUE')




    
![png](output_37_1.png)
    


THE REVENUE ROSE STEADILY BEFORE A MORE PROMINIENT RISE IN 2023

QUESTION 9
What was the Average 'Quantity Sold' & 'Average Revenue' for each product?


USING GROUPBY AND MEAN 


```python
avrg_rev_products = data.groupby("Product")["Revenue"].mean().reset_index()
print(avrg_rev_products)
```

                  Product      Revenue
    0           Beverages  2064.005260
    1             Burgers  7249.996287
    2  Chicken Sandwiches  2204.647981
    3               Fries  2464.201771
    4       Sides & Other   999.996000
    

1. Beverages average revenue is   2064.005260
2.Burgers average revenue is  7249.996287
3.Chicken  average revenue is Sandwiches  2204.647981
4. Fries  average revenue is  2464.201771
5.Sides & Other  average revenue is  999.996000

QUESTION 10 
What was the total number of orders or sales made?


```python
total_sales = data["Quantity"].sum()
print("The total numberws of sales made is  ", total_sales)
```

    The total numberws of sales made is   116995.31000000003
    
