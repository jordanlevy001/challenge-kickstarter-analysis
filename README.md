# Challenge Kickstarter Analysis with Excel

## Overview of Project

### Purpose

#### The purpose of this analysis is to assist Louise in understanding and visualizing trends in the provided fundraising campaign data. Louise would like to know if and how the launch date and funding goal of campaigns affected the campaign outcome. Louise had previously launched a fundraising campaign for her play *Fever*, which came close to its goal in a short period of time.

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date

#### To effectively visualize and determine the campaign outcomes based on launch date, a pivot table was generated from the Kickstarter data in Excel. But since we are analyzing launch dates it is important to be able to filter the pivot table by both year and parent category. The parent category of focus in this case is theater. And we need a column with just the year of the launch date in the Kickstarter worksheet. So before generating the pivot table, a "Years" column was created in the Kickstarter data using the function YEAR(), to extract the year from each of the launch dates which were written in short date form.

<img width="496" alt="Excel Year Function" src="https://user-images.githubusercontent.com/88804543/129990659-8b36739a-0d55-4b43-b56d-6890f2ace3ba.png">

#### The example photo above shows how the YEAR() function can pull the year from another cell.

#### After selecting all of the Kickstarter data, including the "Years" column, a pivot table was generated. The rows were populated with the "Date Created Conversion". The "Date Created Conversion" box in the "Field Name" dialog box was checked again, after which "Year2" and "Quarters" populated the "Rows" box. We had to remove these by dragging them out of the row box and into the sheet. This removes them from the pivot table. Now the pivot table will show months in the first column on the left. The columns were populated with "Outcomes". The values were populated with the "Outcomes" which are then displayed as "Count of Outcomes". The pivot table columns were filtered and sorted to display "successful, failed, canceled" outcomes only and in that order. Theater was selected within the "Parent Category" filter located above the pivot table.

<img width="328" alt="Table_Theater Outcomes_Launch Date" src="https://user-images.githubusercontent.com/88804543/129990942-66ce223c-36b6-4907-a7a6-bb4177bd9c5b.png">

#### This is the completed pivot table.
#### Then a pivot chart was generated from this pivot table. The chart type was adjusted from the default to a line chart. The chart type can be adjusted by selecting the "Change Chart Type" button. Then you can choose from the chart options provided, where you can select a line with markers chart.

<img width="72" alt="Change Chart Type Icon" src="https://user-images.githubusercontent.com/88804543/129991055-765a93e6-dd99-429c-99e0-277a2337cc20.png">
<img width="530" alt="Chart Type to Line" src="https://user-images.githubusercontent.com/88804543/129991065-e93373b9-f130-42e1-9604-51a88cdc7e89.png">

#### After changing the chart type to a line with markers chart, the final graph looks like this:

![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/88804543/129991131-a1abcb0a-2401-4208-ad50-ee78cc8f4b39.png)


### Analysis of Outcomes Based on Goals

#### To calculate and visualize the percentage of: successful, failed, canceled plays based on the funding goal amount, a new worksheet needed to be generated. In the new worksheet, the following columns were created
#### - Goal
#### - Number Successful
#### - Number Failed
#### - Number Canceled
#### - Total Projects
#### - Percentage Successful
#### - Percentage Failed
#### - Percentage Canceled

<img width="1104" alt="Columns and Rows for Outcomes Based on Goals" src="https://user-images.githubusercontent.com/88804543/129991486-39e96f19-afdc-41f9-9a06-83c26835aef5.png">

#### For our analysis, it was helpful to group the goal amounts into dollar-amount ranges. In the "Goal" column on the left, the dollar-amount ranges were designated as follows:

<img width="117" alt="Goal Amounts Grouped" src="https://user-images.githubusercontent.com/88804543/129991544-e55496f0-8ad4-48e2-8838-f72b910ddd1f.png">

#### To populate the "Number Successful", "Number Failed", "Number Canceled" columns, we used the COUNTIFS() function. By using the COUNTIFS() function, we were able to filter the data to count cells which matched our designated criteria. For this table, we used the COUNTIFS() function to count cells with the following criteria:
#### 1. Subcategory: plays
#### 2. Outcome: successful/failed/canceled (designate 1)
#### 3. Goal: corresponding to the dollar-amount range on the left in column A

#### This is what the formula looked like for the first row of the table in the "Number Successful" column, where the goal amount was less than 1000:
<img width="566" alt="Excel COUNTIFS Function1" src="https://user-images.githubusercontent.com/88804543/129991987-b37c0db7-bbbd-4fc0-ad48-71fd60e08bb0.png">

#### For all 3 columns "Number Successful", "Number Failed", "Number Canceled", the COUNTIFS() formula is needed to filter the Kickstarter sheet in column R($R:$R), which is the "Subcategory" for "plays". In the Kickstarter sheet, column D is where the goal amount is located, so we selected the entire column ($D:$D). And we want to count cells with goal amounts less than 1000("<1000"). The dollar signs ($) lock the cells in the formula so they do not change if you copy and paste the formula or drag it into another cell. In the Kickstarter sheet, column F is the "Outcome". We want to filter for only "successful" outcomes in all of column F ($F:$F); so the whole column is selected and our criteria is "successful".

#### Within the "Number Successful" column, the only difference in the formulas between rows is the goal amounts (column D in the Kickstarter worksheet). The next goal range is 1000 to 4999, so the second row in the "Number Successful" column will contain the formula:

<img width="734" alt="Excel COUNTIFS Function2" src="https://user-images.githubusercontent.com/88804543/129994136-3cb7b76b-c9b6-4956-b50c-05e6d3a62e9d.png">

#### You can see that the cells to be counted in the "Goals" column D in the Kickstarter worksheet are greater than or equal to 1000 (">=1000") and less than or equal to 4999 ("<=4999"), which is denoted in the formula.

#### After populating all of the rows within the "Number Successful" column, we move over to the "Number Failed" column. The difference in the formula between cells is the outcome column (F) in the Kickstarter worksheet. We edit the formula to count cells in column F on the Kickstarter worksheet that contain the outcome "failed". See the example:

<img width="708" alt="Excel COUNTIFS Function3" src="https://user-images.githubusercontent.com/88804543/129994253-36fbc799-d677-42b2-a601-49fb0fcd4570.png">

#### For the same row in the "Number Canceled" column, the formula would be adjusted to filter for the outcome: canceled. The formula looks like this:
<img width="727" alt="Excel COUNTIFS Function4" src="https://user-images.githubusercontent.com/88804543/129994505-468831f5-54e2-4c9b-8a45-045497cb00b0.png">

#### After the "Number of: Successful, Failed, Canceled" columns were populated, we wrote a formula to calculate the "Total Projects" column. We did this by summing the corresponding "Number Successful" with the "Number Failed" and the "Number Canceled". We used the function SUM(). In this example, we are summing cells B3 to D3. The formula in action with the involved cells highlighted looks like this:
<img width="527" alt="Excel Total Projects Example" src="https://user-images.githubusercontent.com/88804543/129994677-5a439f17-92d2-4c8a-96e7-3b0ac8c39e56.png">

#### This formula was then dragged down to fill all of the rows below it within Column E.

#### To calculate the values in the next column, "Percentage Successful", we needed to take the "Number Successful" (column B) and divide it by the "Total Projects" (column E). You can multiply this value by 100% to put it in percent form, or you can designate the format of the cell as "Percentage", as I did in this example. When changing the cell to "Percentage" format, Excel automatically moves the decimal 2 places to the right of the current number in the cell, which is equivalent to multiplying the value by 100%. Here is what the box format looks like when "Percentage" is designated:

<img width="169" alt="Excel Percentage Format" src="https://user-images.githubusercontent.com/88804543/129994995-d35d5bb3-fcb3-4e96-8eea-4397eec9618c.png">

#### The formula to calculate the "Percentage Successful" looked like this:
<img width="660" alt="Excel Percentage Successful Formula" src="https://user-images.githubusercontent.com/88804543/129995103-5d8ff5ed-626d-4caa-b3a7-a8d8c60685c4.png">

#### Then you can drag the formula down to populate the rows below it within column F. The same type of calculation is repeated for the "Percentage Failed" and "Percentage Canceled" columns. Please see the following:
<img width="913" alt="Excel Percentage Failed Formula" src="https://user-images.githubusercontent.com/88804543/129995196-7704ff53-88b1-40f0-a8fa-cd639cb8e017.png">
<img width="917" alt="Excel Percentage Canceled Formula" src="https://user-images.githubusercontent.com/88804543/129995204-d1f97518-d48f-4df4-a692-ea8dca2bb8d0.png">

#### It is important to emphasize that all of the cells from F2 to H13 above, are designated as percentages, which is why the formulas do not include a multiplication by 100 component.
<img width="169" alt="Excel Percentage Format" src="https://user-images.githubusercontent.com/88804543/129995276-368ce27c-2b29-44ba-ae8d-55b786c08c28.png">

#### To generate the line chart from this data, I highlighted all cells, then inserted a line chart.
<img width="1128" alt="Inserting a Line Chart" src="https://user-images.githubusercontent.com/88804543/129995323-d518d54f-c7a4-4e13-9e5c-dc7adfd9faa0.png">
<img width="898" alt="Selecting Data" src="https://user-images.githubusercontent.com/88804543/129995354-ef367659-56fd-4865-b597-a9cbea60f164.png">

#### The graph that is automatically generated has too much information and we need to remove the excess.This can be done by selecting the chart, then choosing "Select Data" from the "Chart Design" ribbon at the top. Under 'Legend entries', we can remove the top 4 items, by pressing the minus sign in the bottom left corner below the box. This will leave us with the information we DO want:
#### *"Percentage Successful"
#### *"Percentage Failed"
#### *"Percentage Canceled"
#### In the box that says "Chart Title", the text was edited to "Outcomes Based on Goals". The finalized chart looks like this:
![Outcomes_vs_Goals](https://user-images.githubusercontent.com/88804543/130123811-b262797c-98bc-4346-b871-5d8fe1883d61.png)

### Challenges
#### No challenges occurred while completing deliverable 1 and 2, the outcomes based on launch date and the outcomes based on goals charts. The first challenge occurred when writing the analysis report in the README.md file in GitHub, I had difficulty with the headers. Some headers would display normally but then others would not. This trouble occurred specifically for H4 headers, meaning the ones requiring 4 hashes. Some of the lines with 4 hashes would display normally and others would not. I looked up Markdown syntax to ensure I was using the hashes correctly. I also googled if anyone also had this same issue. I tried to understand why some H4 headers were formatted correctly while others were not. This lead me to the discovery of adding spaces between lines of text and images. So I added space between lines with H4 headers that came after an image. This solved the issue. So I went through the README.md file and added space where it was needed between images and H4 headers.

## Results

![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/88804543/130140643-8a980a74-e38e-472c-a84b-b98089c27af0.png)

### The first conclusion we can draw from the "Outcomes Based on Launch Date" line graph is there are more campaigns launched overall in May, June, July. The second conclusion we can draw is campaigns launched in May had a higher incidence of success. Louise should launch future campaigns in May.

![Outcomes_vs_Goals](https://user-images.githubusercontent.com/88804543/130140672-c0e9f401-9056-4b09-9294-3c5050c48cec.png)

### From the "Outcomes Based on Goals" chart, we can conclude that campaigns with lower goals are more successful. Campaigns with goals less than $5000 had the highest incidence of success.

### There are some limitations to this dataset. This dataset does not tell us background or demographic information about the backers, the people who are donating the money. It would be helpful to know demographic information about the backers because it would help Louise understand who her target demographic should be for her play's fundraising campaign.

### In addition to the graphs shown above, another helpful table we could create would show how close the failed campaigns for the subcategory plays came to reaching their corresponding goal. Examining the failed campaigns for the subcategory of plays, we could calculate what percent of the goal money was pledged. Then we could visualize the percentage funded of the failed campaigns with a histogram. Furthermore, we could also analyze the successful play campaigns and look deeper at how much they exceeded their goal. We could calculate from the subcategory of plays with a successful outcome, how much greater the pledged amount was compared to the goal amount. In other words, determine the percent funded of the successful campaigns for plays. The percentage funded of the successful campaigns could then be visualized with a histogram.

### We could also create a table to analyze how the length of time of the campaign affected the outcome. We would visualize this data with a stacked bar graph comparing the duration of the campaign to the campaign outcome.
