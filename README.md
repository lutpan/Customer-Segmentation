# Customer-Segmentation
In this project i try to solve unsupervised machine learning problem on  dataset where the company is UK-based and registered non-store online retail. The most customer of this company are wholesalers. The original data set came from UCI Machine Learning Repository http://archive.ics.uci.edu/ml/datasets/online+retail and there is also available on kaggle https://www.kaggle.com/carrie1/ecommerce-data.

## Goals
Set the class and the segment label of each customer and grouping into several segments which aims to how the company will treat customers in the future.

## Features
- InvoiceNo: Invoice number. Nominal, a 6-digit integral number uniquely assigned to each transaction. If this code starts with letter 'c', it indicates a cancellation.
- StockCode: Product (item) code. Nominal, a 5-digit integral number uniquely assigned to each distinct product.
- Description: Product (item) name. Nominal.
- Quantity: The quantities of each product (item) per transaction. Numeric.
- InvoiceDate: Invice Date and time. Numeric, the day and time when each transaction was generated.
- UnitPrice: Unit price. Numeric, Product price per unit in sterling.
- CustomerID: Customer number. Nominal, a 5-digit integral number uniquely assigned to each customer.
- Country: Country name. Nominal, the name of the country where each customer resides.


Since this dataset is a Unsupervised Learning Dataset, therefore i should cluster each customerID to process for further. in this case i labeling each customer id using RFM(Recency, Frequency, Monetary) method and find a way how to treat customer based on their segment depends business action.

## Highlights

So this is the sample of dataset that i use in this project and the descriptive statistics table.
![](https://github.com/lutpan/Customer-Segmentation/blob/main/image/df_sample.png) 
and the descriptive statistics table.
![](https://github.com/lutpan/Customer-Segmentation/blob/main/image/df_statistical_value.png)
- when i see the statistical table i got confused why there are negative values in Qantity and UnitPrice minimum value. So i assume that was canceled order and i drop them negative values.
- i drop the missing values too
- Since then there is no total amount table, i added the 'spend' column which from UnitPrice*Quantity
In this dataframe the amount of customer from UK is so dominating, so i decide to separate those.

### UK Data
in this section ill find which class is suitable for each customerID based on RFM Score and the way to determine the RFM score is :
* Recency = Latest Transaction Date - Last Invoice Data
* Frequency = count of invoice no. of transaction
* Monetary = Sum of total spend for each customer id
![](https://github.com/lutpan/Customer-Segmentation/blob/main/image/RFM_distribution.png)

the RFM value is set now i change them into 5 rank score using quantile method. the lowest the score the better.
after i get all of that, i sum up the rank value RFM to labeled which class is suit for each customer (Diamond, Platinum, Gold, Silver, Bronze).
![](https://github.com/lutpan/Customer-Segmentation/blob/main/image/class_score_distribution.png)

the last is giving the label eachs customerid based on aggregated each RFM scores (115 ,555 ,111 , etc).
![](https://github.com/lutpan/Customer-Segmentation/blob/main/image/Class_Segment_Distribution.png)

### Conclusion


