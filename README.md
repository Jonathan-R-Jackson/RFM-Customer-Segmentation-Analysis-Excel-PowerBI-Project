# RFM Customer Segmentation Analysis

# Snapshot Of Dashboard (Power BI Service)

![Completed_Customer_Segmentation_Dashboard](https://github.com/user-attachments/assets/4a959358-61cc-468e-b78c-ebe3d2b2805b)

### Dashboard Link: [View Dashboard](https://app.powerbi.com/view?r=eyJrIjoiZDNlMDk1M2EtNDA1Zi00YTA0LWFiNGMtOWNjMGQzMzZjZWZhIiwidCI6IjJmMDBkZGQzLTc0NzgtNGQ0YS04MDI0LTJhZDRjNzIxNjdlYyJ9)

## Problem Statement

This project was created to segment customers into grouping subsets based on purchasing behavior to enhance targeted marketing strategies, improve retention rates, and increase revenue for an online retailer based in the UK, using transactional data.

## Introduction

Data segmentation, the process of dividing data into smaller, more manageable subsets to gain a better understanding of an audience, allows businesses to tailor their marketing efforts, improve customer satisfaction, and increase sales. There are various types of data segmentation, such as demographic segmentation, which divides customers based on characteristics like age, gender, or income. The type used in this project is RFM analysis, a form of behavioral segmentation, which allows for customer groupings based on purchase recency, frequency, and monetary value from all invoice transaction data collected from 01/12/2010 to 09/12/2011.

Online Retail Sales Dataset: [Download Original Dataset](https://github.com/Jonathan-R-Jackson/RFM-Customer-Segmentation-Analysis-Excel-Project/blob/main/Online%20Retail%20Sales%20Dataset.xlsx)

## Insights

The following insights can be drawn from the dashboard:

### Total Number of Customers = 4,372

   Best Customers = 4.16% of Total Customers & 36.21% of Total Revenue

   Average Customers = 40.19% of Total Customers & 32.97% of Total Revenue

   Churned Customers = 19.08% of Total Customers & 4.02% of Total Revenue
           
### Most Purchased Items

   Our *Best Customers* and *Loyalists* share the same top 5 most purchased items as our best customers, with the primary difference being the quantity purchased. This leads us to conclude that if we create more special offers on these items through direct communications with the *Loyalists* group, we can potentially increase conversion rates from *Loyalists* to *Best Customers*, generating more business revenue.  
  
### New Customer Statistics 
  
   Total Number of New Customers = 104 (2.38% of Total Customers)

   Average Order Value = $270.04

   Top 3 Most Purchased Items:

     1. Rabbit Night Light - Quantity Purchased: 3,550
     2. Sombrero - Quantity Purchased: 2,600
     3. Metal Sign "Take It Or Leave It" - Quantity Purchased: 1,404

## Project Procedural Steps Taken 

- **Step 1**: Open the dataset in Microsoft Excel.

- **Step 2**: Freeze the top header row, change the fill color to blue, and text color to white for enhanced readability.
- **Step 3**: Create a new column titled "ProductAmount" that multiplies the "Quantity" and "UnitPrice" columns (as shown below).

  ![ProductAmount_Column_Formula](https://github.com/user-attachments/assets/a6eb9f31-f819-4cf1-ae57-1f8f87b55fe4)

- **Step 4**: Change the data type of the "ProductAmount" and "UnitPrice" columns to custom currency using English (United Kingdom) for the symbol since this online retailer is based in the UK (as shown below).

  ![Datatype_Change_To_Currency](https://github.com/user-attachments/assets/bde73c0b-a923-49ce-a534-829f5662c69a)

- **Step 5**: To aggregate the data on the customer level, select the dataset and create a pivot table using "CustomerID" for rows and the max of "InvoiceDate", count of "InvoiceNo", and average of "ProductAmount" as the summarized values (as shown below).

  ![Pivot_Table_Summarized_Values](https://github.com/user-attachments/assets/042b20a6-3064-4536-870a-65d5494d572b)

- **Step 6**: Create a new sheet titled "RFM Scores," then copy the data displayed from the pivot table and paste only the values into the "RFM Scores" sheet.
- **Step 7**: Create three new columns to the right of the table with the headers "Recency," "Frequency," and "Monetary."
- **Step 8**: In the second row of the "Recency" column, use the "PERCENTRANK.EXC" function to rank the recency of customers' last purchases. The full formula is `=PERCENTRANK.EXC(B:B,B2,1)*10`, where "B:B" is the array, "B2" is the value being ranked, and 1 is the number of decimal places. The function will return a rank between 0.0 and 0.9, which is then multiplied by 10 to produce a whole number.
- **Step 9**: Use the Autofill handle to apply the formula across all rows, including the "Frequency" and "Monetary" columns.

- **Step 10**: Change the header in Cell A1 from "Row Labels" to "CustomerID" and change the datatype of the values in the "Max of InvoiceDate" column from *General* back to *Date* (as shown below).

  ![RFM_Tab_Completed](https://github.com/user-attachments/assets/36a37203-eec8-435a-b6e6-02e26a306616)

- **Step 11**: Ensure the spreadsheet is saved as an .xlsx file for import into Power BI.

- **Step 12**: Import the .xlsx file into Power BI, selecting the "Online Retail" and "RFM Scores" sheets, then click *Transform Data* to perform necessary data cleaning processes.

  ![Import_xlsx_File_Into_Power_BI](https://github.com/user-attachments/assets/0e7d6b14-0625-4515-ab4b-b320f2537353)

- **Step 13**: In the "RFM Scores" table, change the datatype of "Average of ProductAmount" from *Decimal Number* to *Fixed Decimal Number*, since this column refers to monetary values. Repeat this for the following columns:

  * "Max of InvoiceDate" to *Date* (from *Date/Time*)
  * "StockCode" and "InvoiceNo" to *Text* (from *Text & Whole Numbers*)
  * "UnitPrice" and "ProductAmount" to *Fixed Decimal Number* (from *Decimal Number*)

  ![Datatype_Change_To_Fixed_Decimal_Number](https://github.com/user-attachments/assets/7a36c4c5-bf88-4256-9153-c728ac4700a5)

- **Step 14**: Use the *Split Column* tool to separate the "InvoiceDate" column into two columns: "InvoiceDate" and "InvoiceTime" using the *space* delimiter.

- **Step 15**: *Close & Apply* the pending changes in the Query Editor.

- **Step 16**: In the Model View, change the format of the "RFM Score" column in the "RFM Scores" table to three digits, ensuring that leading zeros are displayed.

  ![WFM_Score_Custom_Format](https://github.com/user-attachments/assets/d4a2bd70-730c-4a87-a946-10094c7bf4cc)

- **Step 17**: Ensure the tables have a correct relationship of Many to 1 from the "Online Retail" table to the "RFM Scores" table, joined on the "CustomerID" columns. Also, switch the cross-filter direction in the relationship to both.

  ![Table Relationships](https://github.com/user-attachments/assets/a394e3f0-35cc-407f-920a-9f6048afbc50)

- **Step 18**: In the *Table View*, create a new column to classify each customer into a group using the RFM Score on the "RFM Scores" table. Use *Table Tools > New Column* to add the following DAX formula to assign customer segment types (as shown below).

  ![Create_Customer_Segment_Column](https://github.com/user-attachments/assets/f7d2ea4f-bb87-4550-8036-102320cb5d9f)

- **Step 19**: Create two additional tables. The first, "Invoice Totals," contains two columns: "InvoiceNo" and "Invoice Total," generated using the following DAX query (as shown below). This can be used for enhanced chart creation.

  ![Create_New_Table](https://github.com/user-attachments/assets/e5cc26bb-18f6-4973-9867-d1c673a55706)

- **Step 20**: Create a new relationship joining the "Invoice Totals" and "Online Retail" tables.

  ![Create_New_Relationship](https://github.com/user-attachments/assets/005505fd-9e60-402d-92ab-6c502b0cf671)

- **Step 21**: The second table, "Customer Segment Strategy," contains curated marketing strategies based on common practices tailored to each customer segment, created using DAX (as shown below).

  ![Create_Customer_Segment_Strategy_Table](https://github.com/user-attachments/assets/84f60354-4e86-4e2b-9328-e40a3fdbeab2)

- **Step 22**: Ensure the relationship between the second table and the "RFM Scores" table is correctly formed.

  ![Customer_Segment_Relationship](https://github.com/user-attachments/assets/785234cf-1026-41b5-9bb4-43da037bf4b6)

- **Step 23**: In *Report View*, create seven different visualizations and one dynamic textbox. One of these is a treemap that shows the various customer segments. Users can either select a segment to filter the other visualizations or hover over it to view total revenue and the number of customers belonging to that segment.

  ![Tree_Map_Details](https://github.com/user-attachments/assets/ae3b41eb-140b-4e19-a5d4-034417e0eeda)

---
