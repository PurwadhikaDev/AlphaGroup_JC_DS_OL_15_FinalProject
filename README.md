This repository is reserved for the final project results made by Group Alpha of JCDSOL-015 by:

- Matthew Adi Simanjaya
- Arga Taufiq Fairuza
- Irma Lusyana Manik

# **ATTENTION!**

The fully-processed dataframe available after the running of the .ipynb is too big to be put in Github. It is hence deposited in Google Drive via this link: https://drive.google.com/drive/folders/1iuGwJI5c9hYH0dBaCrJAi6nJRqUefACW?usp=sharing

## Update 27/11/2024:

Uploaded the final file needed to make the .ipynb notebook run: the brazil-states.geojson.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Update 26/11/2024:

To the README:
- Added links in the README to the datasets used for this project (and uploaded the relevant source materials from those links into the repository), added a screenshot of the Tableau dashboard, and expanded the summary of the README.

To the Notebook:
- Added Version 2.1, that corrects the values for the calculation of the target freight value-to-price ratio for the 'Lost' and 'Potential' seller clusters.
- Added explanations to the problem statement that further pinpoint the goals set for this notebook.
- Changed the suggested deadlines for some of the recommendations section in the notebook.
- Added an overall main target at the recommendations section in the notebook: a minimum retention rate to be maintained for a certain duration.

Link to all the core datasets used for this project: https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce?resource=download&select=olist_orders_dataset.csv

We also used a .geojson file from this link: https://github.com/codeforgermany/click_that_hood/blob/main/public/data/brazil-states.geojson

![Screenshot (4736)](https://github.com/user-attachments/assets/9baf095e-0c93-40f3-8a75-e52472d695f3)

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

This README contains information about the relevant files for Group Alpha's Final Project in the JCDSOL-015 Online Bootcamp in Purwadhika for Data Science and Machine Learning. A .ipynb file containing the finished workbook can be found here.

In addition, a link to the Tableau Public Dashboard can be found here: https://public.tableau.com/app/profile/matthew.adi.simanjaya/viz/FinalProjectTake2_17320184760420/BirdsEyeView?publish=yes

The notebook encompasses the following topics relevant to the Final Project:

- It gives a quick run-down of what Olist is, and what problems face SaaS startups like it.
- It goes through the datasets provided in the Kaggle one by one, containing data dictionaries and examples of its rows and columns, and how they are merged to make the main dataframe for this notebook.
- It checks for incorrect DTypes, Missingno and Outliers in the notebook, and later deals with them in the Data Cleaning Phase.
- A cohort analysis is created with the cleaned dataframe, followed by manual definition of RFM Scores and segmentation of sellers by these Scores into clusters.
- The same clustering process is then done using K-Means (the result of which was later accepted) and DBSCAN, and all three clustering methods were later compared.
- Using K-Means's interpretation of the clusters, we then profiled the sellers by location, R, F and M values, by seller count and monetary value contribution, and analyzed their behaviors using information available in our dataframe.
- We make our conclusions based on our analysis and make suggestions and recommendation to Olist to best improve the retention rate of their less active sellers, and squeeze more value from their more active sellers.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Background

Olist is a service provider for businesses, Brazilian e-commerce platform that helps small and medium-sized businesses sell their products on major online marketplaces. It acts as an intermediary, allowing these businesses to reach a wider audience by listing their products on multiple e-commerce platforms, including some of the big names in Brazil. Olist takes care of the logistics, customer service, and other aspects, making it easier for businesses to sell online (B2B2C). The primary goals of this platform is to simplify the e-commerse process, enabling business to focus on growth and customer engagement.

There are 5 products and services by Olist, namely:

- Olist Store: A platform that enables sellers to list and sell their products across multiple major Brazilian marketplaces, providing centralized management and logistics support.
- Olist Hub: A service that manages seller accounts across sales channels, optimizing product listings and pricing for marketplace fulfillment.
- Olist Envios (Olist Shipping): A logistics service integrated into the Olist platform, facilitating product delivery through Olist's logistics partners.
- Olist Tiny: An ERP system that simplifies business operations and automates workflows, supporting growth across various business sizes and sectors.
- Olist Vnda: An omnichannel e-commerce platform offering advanced technology and integrated resources to boost business growth.

One of article in 2021 explain that the company wants to go beyond marketplaces, and the new capital will enable it to offer a fulfillment operation, set to open early in 2022, as well as financial services. Retailers on Olist already have access to credit lines for working capital, but the company plans to expand that technology to include risk management, accelerated sales and internal credit models for merchants

Source:

- https://pitchbook.com/profiles/company/102473-65#overview
- https://techcrunch.com/2021/12/15/brazils-olist-gets-its-horn-with-new-186m-funding-round/
- https://www.crunchbase.com/organization/olist

# Problem Statement and Goals

Olist, a Brazilian e-commerce platform that supports small and medium-sized businesses by facilitating sales through major online marketplaces, faces a significant challenge in seller retention. Despite its role in simplifying e-commerce processes and enabling sellers to focus on growth, recent trends indicate a decline in seller retention. This issue threatens the sustainability of Olist's business model, as retaining active and high-performing sellers is critical to getting more Lifetime Value (LTV) from each seller (Source: https://www.google.com/url?q=https%3A%2F%2Fuserpilot.com%2Fblog%2Fsaas-customer-retention%2F), thus maintaining platform engagement and revenue.

To address this, Olist has implemented a rule-based RFM (Recency, Frequency, Monetary) clustering approach to segment sellers based on their transaction behaviors. However, this static method may not fully capture the dynamic nature of seller performance and market trends, raising the question of whether machine learning-based clustering could provide a more accurate and actionable segmentation.

The primary objective of this project is to explore how sellers can be clustered using RFM analysis to determine which clusters they belong to in terms of their activity and total transaction value, which can act as a base for us to analyze ways to minimize churn rates. This involves evaluating the effectiveness of machine learning (ML)-based clustering compared to the existing rule-based approach, profiling them, identifying meaningful patterns in seller behavior, and leveraging these insights to develop strategies that improve retention and engagement. By refining the seller clustering methodology, Olist aims to maintain and optimize the sellers retention rate.

Action: Sellers Clustering

Goal: Improve the clustering of these sellers using ML techniques to improve our ability to analyze these sellers based on their behavior.

Problem Statement for Analytics:
After the seller clusters have been determined, we will then analyze each of these clusters to profile the sellers and see their differences in behavior based on RFM, particularly those that directly affect Olist's bottom line.

To optimize seller retention, it is essential to gain a comprehensive understanding of seller behavior and performance. This begins with building a cohort analysis to track and analyze seller activity over time, helping to identify trends in retention and churn rates. Additionally, understanding the geographical distribution of the most active sellers will provide insights into regional variations in seller performance and help prioritize areas for targeted intervention. Investigating the types of products sold by these active sellers can shed light on which categories drive engagement and revenue, enabling tailored strategies to boost sales in those segments.

Furthermore, determining which seller segments should be prioritized for retention efforts—based on their RFM scores and contribution to overall platform performance—will ensure that resources are allocated effectively. By combining these insights, Olist can develop targeted strategies to minimize the decline in seller retention, fostering a sustainable and thriving marketplace.

Action: Profiling clusters by location, seller count and value contribution and analyzing seller behavior by products sold, RFM values and freight costs.

Goal: Optimizing sellers retention by decreasing the freight cost-to-price ratio by 25% for the lowest-performing sellers, increasing the minimum sellers' transaction frequency to 15 per month (for those that still have potential to become loyal sellers), and restore the transaction frequency and monetary value of the best-performing sellers back to their peaks by the end of the year.

# Analytical Flow of the .ipynb Notebook

- We first went through a data dictionary of the rows for each dataset that will make up the first iteration of the dataframe, and then end with the actual formation of the dataframe based on how we joined the datasets
- We performed the Data Understanding Phase, checking this dataframe for missingno, outliers, and other suspicious values, and the appropriate actions are to be summarized there and acted upon in the Data Cleaning Phase.
- We performed an EDA to determine which directions we can take the analysis of the data that will be relevant for our goals in this notebook.
- Unneeded or problematic values detected in the Data Understanding Phase are deleted in the Data Cleaning Phase, and new columns are added in the Feature Engineering phase to further expand the available directions our analysis can go.
- A cohort analysis was made first, and then RFM Values and Scores were determined as prior use for the Clustering methods we were to use.
- Three clustering methods (Manual, K-Means and DBSCAN) were trialed to cluster the sellers by their RFM Values/Scores (it is later determined that the K-Means methodology created the clusters best suited for analysis).
- Using K-Means's interpretation of the clusters, we then profiled the sellers by location, R, F and M values, by seller count and monetary value contribution, and analyzed their behaviors using information available in our dataframe.
- We made our conclusions based on our analysis and make suggestions and recommendation to Olist to best improve the retention rate of their less active sellers, and squeeze more value from their more active sellers.

# Limitation

- The datasets analyzed had inherent duplicates in order_id and we found it difficult to remove all of them. Hence, we try not to use the joined dataframe as is (instead we call the dataframe by way of .groupby() operations.)
- We have used Order Value per Product (price + freight_value) instead of directly using payment_value for calculation purposes because the calculated payment value and the actual payment value are different, and we found no literature on either Google or Kaggle on why this is. This is done in order to make our numbers more consistent.
- The timeframe of the dataframe goes from 5/9/2016 to 12/11/2018.

# Conclusion:

- K-Means Clustering Success: K-Means more effectively clustered sellers into four distinct groups based on their RFM scores, generating more solid clusters than the rule-based original. This segmentation provides valuable insights into sellers’ characteristics, which can be leveraged to optimize Olist's revenue and improve seller retention strategies.
- Potential Sellers' Performance: Despite being the highest contributors to Olist's total order value, 'Potential' sellers are placed in the lower-end of the overall RFM score spectrum. Many of these sellers have high recency values (over 50 days without an order passing through Olist), low transaction frequency, and low monetary value per seller, indicating they are less engaged or effective in terms of long-term sales consistency.
- Declining Order Count from Champions and Loyal Sellers: Since 2018, 'Loyal Sellers' and 'Champions' have experienced a decline in transaction frequency and total order value. While this could have external factors, such as these stores having less orders overall, efforts to further engage them to use Olist's services could prove beneficial, as their products tend to be priced higher.
- Lost Sellers' Activity: 'Lost' sellers have not made any transactions since late 2017, indicating that they are no longer active in the market. This segment is essentially inactive, and trying to get these sellers to rejoin Olist could cost more than their potential gains to Olist.

# Recommendation:

## Potential:

- Coordination with partner ecommerce platforms to use bundling and flash sales to increase AOV, especially on products with declining AOV:
  - Find ways to convince the sellers in Olist to focus on top-selling products with declining AOV. These efforts can encourage higher-order values, especially during seasonal times, while ensuring the promotions align with profitability margins.

  - Strategy: Coordinate with multiple major Brazilian marketplaces from 'Olist store' a flash sale event during the second quarter of the year, as this period has the highest frequency of transactions. Leveraging this peak activity can drive even higher sales, attract more buyers, and encourage customer engagement. The event can be tailored to include discounts, bundling offers, and exclusive deals to maximize participation and revenue.

  - Output: Decrease Recency value to less than 50 days without an order passed through Olist and increase Frequency (to 15 orders/month), and Monetary values (to at least 20k Brazilian Reals total) of 558 of the 1,116 'Potential' sellers aforementioned deemed as 'declining'. These goals are to be achieved by the end of 2019.

The main products are sports_leisure, health_beauty, housewares, auto, furniture_decor, cool_stuff, computers_accessories, baby, toys, garden_tools

- Encourage bundling of smaller products to reduce freight-to-price ratio:
  - Encourage sellers to bundle smaller, lighter items to minimize freight costs per unit. This strategy can improve customer satisfaction and increase order frequency and monetary value.
  - Olist can try using a 'cargo-sharing' system, where goods from multiple sellers going to customers within close proximity go into a single cargo vehicle.
  - Given that this is a major shift in shipping strategy, a pilot plan should be performed by the second month after the publishing of this notebook. At least 33% of cargo transports should use this system within one year of this notebook's publishing.
  - Offer "freight-free" promotions for bundles to further incentivize purchases.
  - The goal is to cut the median freight cost-to-price ratio for the 'Potential' and 'Lost' clusters down by 25% by next year.

## Loyal Sellers & Champions:

- Loyalty program with convertible points and exclusive access to specialized services to better sell their wares:
  - Introduce a loyalty program with rewards in the form of convertible points. Offer specialized or customized services tailor-made to suit their business, or give them temporary free shipping or lower markup on their prices.
  - Strategy: Implement tier-based loyalty rewards (e.g., Silver, Gold, Platinum), motivating sellers to increase sales and stay engaged with Olist.
  - Output: Get the Frequency of Loyal Sellers and Champions back to their peaks in this dataframe. This increase is to be reached by the end of 2019.

- Bundling and recommending higher-end products through seasonal marketing:
  - Implement a bundling strategy that emphasizes higher-end products, recommended through seasonal marketing campaigns, to maintain the performance and profitability of Loyal Sellers and Champions.

  - Coordinate these marketplaces to also run personalized email marketing campaigns that offer tailored product recommendations based on past sales, ensuring the higher-end products are effectively promoted.
  - Output: Get the Monetary Value of Loyal Sellers and Champions back to their peaks in this dataframe. This increase is to be reached by the end of 2019.

Higher-end products are watches_gift, bed_bath_table, and furniture_decor

## Lost:

- Not investing in the Lost segment:

Given the minimal contribution of Lost sellers to Olist’s total order value and their inactivity for over a year, focus on active and potential sellers. The resources may be better allocated elsewhere to boost retention and engagement with more promising segments.
Sending low-cost re-engagement emails or small incentives to revive interest, such as offering discounted listing fees, just to keep the door open for possible returns.

Overall, we hope that these recommendations will help increase the retention rate of Olist's sellers. We believe that achieving a stable sellers' retention rate at above 35% for at least 12 months since their first order through Olist should be possible by the end of 2019.
