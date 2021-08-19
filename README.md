# Challenge Kickstarter Analysis with Excel

## Overview of Project

### Purpose

#### The purpose of this analysis is to assist Louise in understanding and visualizing trends in the provided fundraising campaign data. Louise would like to know if and how the launch date and funding goal of campaigns affected the campaign outcome. Louise had previously launched a fundraising campaign for her play Fever, which came close to its goal in a short period of time.

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date

#### To effectively visualize and determine the campaign outcomes based on launch date, a pivot table was generated from the Kickstarter data in Excel. But since we are examining launch dates it is important to be able to filter the pivot table by both year and parent category. The parent category of focus in this case is theater. So before generating the pivot table, a "Years" column was created in the Kickstarter data using the function YEAR(), to extract the year from each of teh launch dates which were written in short date form.

<img width="496" alt="Excel Year Function" src="https://user-images.githubusercontent.com/88804543/129990659-8b36739a-0d55-4b43-b56d-6890f2ace3ba.png">
#### The example photo above shows how the YEAR() function can pull the year from another cell.

#### After selecting all of the Kickstarter data, including the "Years" column, a pivot table was generated. The rows were populated with the "Date Created Conversion". The columns were populated with "Outcomes". The values were populated with the "Outcomes" which are then displayed as "Count of Outcomes". The pivot table columns were filtered and sorted to display "successful, failed, canceled" outcomes only and in that order. Theater was selected within the "Parent Category" filter.
<img width="328" alt="Table_Theater Outcomes_Launch Date" src="https://user-images.githubusercontent.com/88804543/129990942-66ce223c-36b6-4907-a7a6-bb4177bd9c5b.png">
#### This is the completed pivot table. 
#### Then a pivot chart was generated from this pivot table. The chart type was adjusted from the default to a line chart. The chart type can be adjusted by selecting the "Change Chart Type" Button that looks like this:
<img width="72" alt="Change Chart Type Icon" src="https://user-images.githubusercontent.com/88804543/129991055-765a93e6-dd99-429c-99e0-277a2337cc20.png">
<img width="530" alt="Chart Type to Line" src="https://user-images.githubusercontent.com/88804543/129991065-e93373b9-f130-42e1-9604-51a88cdc7e89.png">
#### After changing the chart type to a line with markers chart, the final graph looks like this:
![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/88804543/129991131-a1abcb0a-2401-4208-ad50-ee78cc8f4b39.png)

### Analysis of Outcomes Based on Goals

#### To calculate and visualize the percentage of successful, failed, canceled plays based on the funding goal amount, a new worksheet needed to be generated. In the new worksheet, the following columns were created
#### *Goal
#### *Number Successful
#### *Number Failed
#### *Number Canceled
#### *Total Projects
#### *Percentage Successful
#### *Percentage Failed
#### *Percentage Canceled

<img width="1104" alt="Columns and Rows for Outcomes Based on Goals" src="https://user-images.githubusercontent.com/88804543/129991486-39e96f19-afdc-41f9-9a06-83c26835aef5.png">

#### For our analysis, it will be helpful to group the goal amounts into dollar-amount ranges. In the "Goal" column on the left, the dollar-amount ranges were designated as follows:
<img width="117" alt="Goal Amounts Grouped" src="https://user-images.githubusercontent.com/88804543/129991544-e55496f0-8ad4-48e2-8838-f72b910ddd1f.png">

#### To populate the "Number Successful", "Number Failed", "Number Canceled" columns, we used the COUNTIFS() function. By using the COUNTIFS() function, we can filter the data to count cells which match our designated criteria. For this table, we will use the COUNTIFS() function to count cells with the following criteria:
#### 1. Subcategory: plays
#### 2. Outcome: successful/failed/canceled (we will choose 1)
#### 3. Goal: corresponding to the dollar-amount range on the left in column A

#### This is what the formula looked like for the first row of the table in the "Number Successful" column, where the goal amount was less than 1000
<img width="566" alt="Excel COUNTIFS Function1" src="https://user-images.githubusercontent.com/88804543/129991987-b37c0db7-bbbd-4fc0-ad48-71fd60e08bb0.png">

#### In the Kickstarter sheet, column D is where the goal amount is located, and we want to count all goal amounts less than 1000 that also meet our other criteria.
