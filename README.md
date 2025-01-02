### Description

For this project I wanted to enhance the supply chain of a company through identifying late deliveries with Machine Learning and conduct an analysis of the feature importance. I also wanted to conduct customer segmentation and Exploratory Data Analysis to get a better undersanding of the company. The notebook is split into three seperate parts. This was all apart of my end of year capstone project so a poster (which you can see at the bottom of this ReadMe), 5,500 word written report and slides from my presentation are also included.

There were two main goals with this project;

1) To try to use machine learning and exploratory data analysis (EDA) on the current data given by the business, to predict whether an order will arrive late or on time.

2) To try to identify distinct customer segments and explore their characteristics.

3) Provide actionable insights.

### Dataset

The full dataset is linked here [Link](https://data.mendeley.com/datasets/8gx2fvg2k6/3)

180,519 entries, total 44 columns - Memory Usage: 60.6+ MB

### Notebook

Models used 

- Nearest Neighbors
- K means clustering
- Support Vectors
- Decision Tree
- Random Forest
- AdaBoost
- Gradient Boosting
- Naive Bayes
- Quadratic DA
- Neural Net

Final model

- XGBoost
- K means clustering
  
### **Insights**
In terms of actionable insights the number 1 action you can take today to drop late deliveries substantially is to increase the estimated delivery time to at least 3 days until the supply chain team can improve the logistics.

I also found that;

- Priority areas for logistics to look into is shipping mode, followed by seasonality of orders (shipping date & order date features)
- I found the shipping mode, days for shipping sheduled two be the two largest contributing features to late deliveries.
- Cluster 6 is the clear high-value group, with high spending and profitability
- Clusters 0, 2, and 3 represent low-valuecustomers who could benefit from strategies to increase profitability or minimize costs
- Cluster 7 shows promise with moderate sales and profitability, making it a potential growth segment

### **Model Results**

| Metric | Value |
| --- | --- |
| Best Score Achieved | 0.82 |
| Accuracy on Training Set | 0.962 |
| Accuracy on Validation Set | 0.819 |
| Recall | 0.74 |
| Customer segments | 8 |
| Silhouette Score | 0.4+ |

<img width="790" alt="Screenshot 2024-12-18 at 09 52 21" src="https://github.com/user-attachments/assets/6acaffef-4a84-4a22-8550-600259551571" />

[Download Capstone Poster (PDF)](https://github.com/user-attachments/files/17661654/Capstone.CA3.Poster.pdf)
