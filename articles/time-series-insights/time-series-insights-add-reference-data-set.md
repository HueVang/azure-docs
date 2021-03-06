---
title: How to add a reference data set to your Azure Time Series Insights environment
description: This article describes how to add a reference data set to augment data in your Azure Time Series Insights environment. 
ms.service: time-series-insights
services: time-series-insights
author: jasonwhowell
ms.author: jasonh
manager: kfile
ms.reviewer: jasonh, kfile, anshan
ms.workload: big-data
ms.topic: conceptual
ms.date: 02/15/2018
---

# Create a reference data set for your Time Series Insights environment using the Azure portal

This article describes how to add a reference data set to your Azure Time Series Insights environment. Reference data is useful to join to your source data to augment the values.

A Reference Data Set is a collection of items that augment the events from your event source. Time Series Insights ingress engine joins each event from your event source with the corresponding data row in your reference data set. This augmented event is then available for query. This join is based on the Primary Key column(s) defined in your reference data set.

Reference data is not joined retroactively. This means that only current and future ingress data is matched and joined to the reference date set, once it has been configured and uploaded.

## Add a reference data set

1. Sign in to the [Azure portal](https://portal.azure.com).

2. Locate your existing Time Series Insights environment. Click **All resources** in the menu on the left side of the Azure portal. Select your Time Series Insights environment.

3. Select the **Overview** page. Locate the **Time Series Insights explorer URL** and open the link.  

   View the explorer for your TSI environment.

4. Expand the environment selector in the TSI explorer. Choose the active environment. Select the reference data icon on the upper right in the explorer page.

   ![Add reference data](media/add-reference-data-set/add_reference_data.png)

5. Select the **+ Add a data set** button to begin adding a new data set.

   ![Add data set](media/add-reference-data-set/add_data_set.png)

6. On the **New reference data set** page, choose the format of the data: 
   - Choose **CSV** for comma-delimited data. The first row is treated as a header row. 
   - Choose **JSON Array** for javascript object notation (JSON) formatted data.

   ![Choose data format.](media/add-reference-data-set/add_data.png)

7. Provide the data, using one of the two methods:
   - Paste the data into the text editor. Then, select **Parse reference data** button.
   - Select **Choose File** button to add data from a local text file. 

   For example, paste CSV data:
   ![Pasted CSV data](media/add-reference-data-set/csv_data_pasted.png)

   For example, paste JSON array data:
   ![Paste JSON data](media/add-reference-data-set/json_data_pasted.png)

   If there is an error parsing the data values, the error appears in red at the bottom of the page, such as `CSV parsing error, no rows extracted`.

8. Once the data is successfully parsed, a data grid is shown displaying the columns and rows representing the data.  Review the data grid to ensure correctness.

   ![Add reference data](media/add-reference-data-set/parse_data.png)

9. Review each column to see the data type assumed, and change the data type if needed.  Select the data type symbol in the column heading: **#** for double (numerical data), **T|F** for boolean, or **Abc** for string.

   ![Choose data types on the column headings.](media/add-reference-data-set/choose_datatypes.png)

10. Rename the column headers if needed. The key column name is necessary to join to the corresponding property in your event source. Ensure that the reference data key column names match exactly to the event name to your incoming data, including case-sensitivity. The non-key column names are used to augment the incoming data with the corresponding reference data values.

11. Click **Add a row** or **Add a column** to add more reference data values, as needed.

12. Type a value in the **Filter the rows...** field to review specific rows as needed. The filter is useful for reviewing data, but is not applied when uploading the data.
 
13. Name the data set, by filling in the **Data set name** field above the data grid.

   ![Name the data set.](media/add-reference-data-set/name_reference_dataset.png)

14. Provide the **Primary Key** column in the data set, by selecting the drop-down above the data grid.

   ![Select the key column(s).](media/add-reference-data-set/set_primary_key.png)

   Optionally, select the **+** button to add a secondary key column, as a composite primary key. If you need to undo the selection, choose the empty value from the drop-down to remove the secondary key.

15.  To upload the data, select the **Upload rows** button.

   ![Upload](media/add-reference-data-set/upload_rows.png)

   The page confirms the completed upload and display the message **Successfully uploaded dataset**.

## Next steps
* [Manage reference data](time-series-insights-manage-reference-data-csharp.md) programmatically.
* For the complete API reference, see [Reference Data API](/rest/api/time-series-insights/time-series-insights-reference-reference-data-api) document.
