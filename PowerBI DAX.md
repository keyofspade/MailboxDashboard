# Manifest Rate Report Page

There are 4 additional columns added and nested inside PowerBI Power Query. These columns are not in the source Sharepoint List and is only in PowerBI. 
These columns generate the necessary manifest order visuals. 

* Values are calculated to be either “Pending” or “Completed” based on C.I Status column

```
CI Pending Status =
    IF(
    OR('C I  Initiation_Sheet'[C.I status]= "Epi-x Posted",
    'C I  Initiation_Sheet'[C.I Status] = "Complete: No CI Needed"),
    "Completed",
    "Pending"
)
```
* Values are the difference in days between “Date Added to Tracker” and “Date MO/CL Submitted” columns
```
Manifest Order Sent Diff = DATEDIFF(
    'C I  Initiation_Sheet'[Date Added to Tracker:].[Date], 
    'C I  Initiation_Sheet'[Date MO/CL submitted].[Date],DAY
    )
```
* Values are the difference in days between “Date MO/CL Submitted” and “Date Manifest Received from Airlines” columns
```
Manifest Received Diff = DATEDIFF(
    'C I  Initiation_Sheet'[Date MO/CL submitted].[Date], 
    'C I  Initiation_Sheet'[Date Manifest Received from Airline].[Date],DAY
    )
```
* Values are the difference in days between “Date Manifest Received from Airlines” and “Date Epi-X posted” columns
```
Epi-X Sent Diff = DATEDIFF(
  'C I  Initiation_Sheet'[Date Manifest Received from Airline].[Date],
  'C I  Initiation_Sheet'[Date Epi-x posted].[Date],DAY
  )
```
### The Diff columns are then averaged to represent the rate seen in the counter cards and visualize with bar graphs for day differences in the report page. 

# Team Report Page
There are 5 additional columns nested in PowerBI. These formulas are integral for the weekly email breakdown visual.
* Identify start date of week to generate week range.
```
Week - Start Date = 
  var _year = 2022
  return
  DATE(_year , 1 , 1) +2 + ('E-mail_Sheet'[Week Number]-1) * 7
```
* Identify end date of week to generate week range.
```
Week - End Date = 
  var _year = 2022
  return
  DATE(_year , 1 , 2) + 1 + ('E-mail_Sheet'[Week Number] - 1 ) * 7 + 6
```
* Identify week number based on date of entry.
```
Week Number = WEEKNUM('E-mail_Sheet' [Date email received],21)
```
* Identify week number based on date of entry
```
Week Range = 'E-mail_Sheet'[Week - Start Date].[Date]& "-" & 'E-mail_Sheet' [Week - End Date].[Date]
```
* Format the date string and remove 2022 from axis labels.
```
Week Short Date = SUBSTITUTE('E-mail_Sheet'[Week Range], "/2022", "")
```
