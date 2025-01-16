# Table of Contents
 - [Executive Summary](#executive-summary)
 - [Key Findings](#key-findings)
   - [Recommendations](#recommendations)
 - [Introduction](#introduction)
 - [Dataset Overview](#dataset-overview)
 - [Methodology](#methodology)
   - [Classification](#part-i-classification)
   - [Segmentation](#part-ii-segmentation)
 - [Results](#results)
   - [Classification](#part-i-classification)
   - [Segmentation](#part-ii-customer-segmentation) 
 - [Insights and Recommendations](#insights-and-recommendations)
 - [Supporting Material](#supporting-material)
   - [Poster](#poster)
   - [Slides](#slides)
   - [Written Report](#written-report)
<a name="headers"/>
 
# Executive Summary
This report focuses on optimizing the supply chain and enhancing customer segmentation for a company using Machine Learning and Exploratory Data Analysis (EDA). The project addresses critical business challenges, including predicting late deliveries, identifying distinct customer segments, and providing actionable insights for operational improvement.

Using a dataset containing 180,519 entries across 44 columns, the analysis was divided into three key components: 
1. **EDA**
2. **Classification**
3. **Clustering**

The classification process tested multiple machine learning models, with **XGBoost** emerging as the most effective, achieving a validation **accuracy of 81.9%** and a **recall of 74%**. Clustering via K-Means identified **8 customer segments**, revealing high-value and low-value groups to guide customer retention and growth strategies.

# Key Findings
  #### Late Delivery Prediction
  •	The top factors contributing to late deliveries are shipping mode and scheduled shipping days.
	•	Increasing the estimated delivery time to at least 3 days will immediately reduce nearly all late deliveries to none.
 
  #### Customer Segmentation:
  •	Cluster 6 represents high-value customers with significant spending and profitability—focus retention efforts here.
	•	Clusters 0, 2, and 3 consist of low-value customers requiring targeted strategies to increase profitability or reduce costs.
	•	Cluster 7 shows potential for growth with moderate sales and profitability, making it a key segment for marketing efforts.
	
  #### Logistics Insights:
  •	Priority areas for improvement include shipping mode optimization and addressing the seasonality of orders (e.g., shipping and order dates).

## Recommendations:
1. Immediate Action: Adjust estimated delivery times to reduce late deliveries while logistics processes are optimized.
2. Customer Retention: Focus retention efforts on high-value segments (e.g., Cluster 6) and explore growth opportunities with moderate-value segments (e.g., Cluster 7).
3. Long-Term Strategy: Collaborate with the logistics team to address key bottlenecks, such as shipping mode inefficiencies and seasonal demand fluctuations.

# Introduction
•	DataCo is a global e-commerce retailer specializing in diverse product offerings, including consumer, corporate, and home office goods, with a focus on optimizing customer transactions, delivery logistics, and market segmentation across regions such as Africa, Europe, LATAM, Pacific Asia, and USCA. They are currently suffering from late deliveries and the head of logistics has tasked us with developing a ML algorhithm to predict late deliveries, report on which features contribute the most to late deliveries, and provide recommendations for how to best move forward with this issue. As well as this, the marketing Director wishes for us to perform customer segmentation to identify current high-value and low-value customers.

# Dataset Overview
The dataset we have been given, is linked here - [Dataset Link](https://data.mendeley.com/datasets/8gx2fvg2k6/5). It has 180,519 entries across 44 columns with a memory usage of 60.6+ MB. It is fairly clean, with some entries in Spanish, or undocumented abbreviations which I just left in the dataset. It was already combined into one csv and had only 3 null values in the ZipCode which I removed.

# Methodology
  ### Part I: Classification
  -	**Models Tested:** Nine supervised classification models, including Random Forest, Nearest Neighbors, Gradient Boosting, and Support Vector Machines, were evaluated. Metrics such as accuracy, recall, precision, F1 score, and ROC-AUC were used to identify top-performing models.
  - **Final Model Selection:** XGBoost was selected as the final model after outperforming other classifiers in recall (74%) and achieving consistent results through cross-validation. Parameter tuning addressed overfitting issues, resulting in the best balance between precision and recall.
  - **Feature Importance:** XGBoost revealed that shipping mode and scheduled delivery days were the most significant predictors of late deliveries, providing actionable insights for improving logistics. Additional interpretability techniques, such as LIME, confirmed these findings and uncovered potential areas for operational improvements.

  ### Part II: Segmentation
  - **Dimensionality Reduction:** Principal Component Analysis (PCA) was used to reduce the dataset to 3 components, addressing dimensionality challenges while retaining key variance in the data. Features were scaled to a mean of 0 and standard deviation of 1 before applying PCA.
  - **Cluster Selection:** The Elbow Method was applied to determine the optimal number of clusters, which suggested 5 clusters. Further refinement using Silhouette Scores led to the selection of 8 clusters to balance clustering performance and business usability.
  - **Clustering Algorithm:** K-Means clustering was applied to the PCA-transformed data. Random state was set for reproducibility, and cluster assignments were added to the dataset for further analysis.
  - **Evaluation:** Silhouette scores were calculated for clusters ranging from 4 to 12 to validate the quality of clustering. A score of 0.425 for 8 clusters was the highest achieved, confirming this as the optimal configuration.

# Results
  ### Part I: Classification
  - **XGBoost Results**
    - Achieved a validation accuracy of 81.9%, a recall of 74%, and a precision of 84.7%, making it the top-performing model in CA3.
    - Slight overfitting was observed, with training accuracy at 96.2%, though the recall score made it suitable for the business goal of predicting late deliveries.
  - **Key influential features:**
    - Shipping Mode: Identified as the most impactful feature in both frequency and gain.
    - Days for Shipment Scheduled, Shipping Date, and Order Date: Highlighted the importance of logistical timing.
    - Secondary features: Order Item ID, Longitude, Market, and Customer City.
	- **LIME Analysis:**
    - Conditions such as longer scheduled shipment times and specific shipping modes significantly reduce the likelihood of late deliveries.
    - Logistical and location-based features play a critical role in delivery predictions.

  ### Part II: Customer Segmentation
  -	PCA and K-Means clustering identified 8 customer segments.
  -	Silhouette Score of 0.425 confirmed the quality of clustering.
  -	Cluster analysis revealed key group characteristics, such as high-value customers (Cluster 6) and low-value customers (Clusters 0, 2, and 3), providing a basis for future segmentation strategies.

# Insights and Recommendations
   **Reducing Late Deliveries**
   - Short-Term Fix: Adjust estimated delivery times to a minimum of 3 days to immediately reduce late deliveries while investigating logistics further.
   - Operational Focus: Prioritize improvements in shipping modes and scheduling to address key factors influencing delays, as identified by XGBoost’s feature importance analysis.

   **Enhancing Customer Segmentation**
   - Focus on Cluster 6 to retain high-value customers through loyalty programs, exclusive offers, and personalized marketing.
   - Develop targeted strategies for Clusters 0, 2, and 3 to either increase profitability or minimize costs, such as discount bundling or cross-selling initiatives.
   - Invest in growth opportunities with Cluster 7 by offering incentives to encourage larger purchases and repeat transactions.

   **Leveraging Geographic Insights**
   - Concentrate marketing efforts in high-value regions, such as North America, while exploring underperforming regions for untapped potential.
   - Evaluate regional logistics efficiency to better serve high-value clusters and reduce delivery risks.

   **Future Analysis**
   - Conduct a time series analysis to detect seasonal demand fluctuations and adjust supply chain operations accordingly.
   - Explore product preferences within customer segments through additional feature engineering to uncover actionable insights for the marketing and product teams.

# Supporting Material
As this was part of my College Capstone project I have the following supporting material alongside the project.
- #### [Poster](https://github.com/user-attachments/files/17661654/Capstone.CA3.Poster.pdf)
- #### [Slides](https://github.com/jasonldoyle/Supply_Chain_Optimisation_and_Customer_Segmentation/blob/main/Video_Slides.pdf)
- #### [Written Report](https://github.com/jasonldoyle/Supply_Chain_Optimisation_and_Customer_Segmentation/blob/main/CA3_Report.docx)
<img width="790" alt="Screenshot 2024-12-18 at 09 52 21" src="https://github.com/user-attachments/assets/6acaffef-4a84-4a22-8550-600259551571" />
