# AlphaGroup_JC_DS_OL_15_FinalProject

## Update 26/11/2024:

Added links in the README to the datasets used for this project, and added a screenshot of the Tableau dashboard.

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
- Using DBSCAN's interpretation of the clusters, we then profiled the sellers by location, R, F and M values, by seller count and monetary value contribution, and analyzed their behaviors using information available in our dataframe.
- We make our conclusions based on our analysis and make suggestions and recommendation to Olist to best improve the retention rate of their less active sellers, and squeeze more value from their more active sellers.
