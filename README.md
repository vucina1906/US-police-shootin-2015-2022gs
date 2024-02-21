In this project, I analyzed the US police shootings dataset from Kaggle, link https://www.kaggle.com/datasets/ramjasmaurya/us-police-shootings-from-20152022/data. First  I analyzed data using Microsoft SQL Server (all queries written in SQL document) and after that created an interactive Power BI Dashboard.
Regarding that we have a date column in the original data, I created a custom date table and connected it to the Police Shooting table. 

On Chart 1 we wanted to see the total number of shootings in the current year and also to have a percentage representation of the difference between shootings in the current year (CY) and the previous year(PY) that the user chose.For Total CY Shootings and YoY growth, we create two new measures using  formulas:
CY Shootings = TOTALYTD(COUNT('US Police shootings in from 2015-22'[id]),'Calendar'[Date])
PY Shootings = VAR PreviousYearShootings =
CALCULATE(COUNT('US Police shootings in from 2015-22'[id]),YEAR('US Police shootings in from 2015-22'[shooting_date]) = YEAR(MAX('Calendar'[Date])) - 1)
RETURN PreviousYearShootings
Then to get YoY growth (difference in the number of shootings in the current and previous year) we create a new measure of YoY Shootings using the formula:
YoY Shootings = ([CY Shootings]-[PY Shootings])/[PY Shootings].

Chart 2 shows  which number of shootings in CY was preceded by a direct attack on an official and also has a percentage representation of the difference between CY and PY.

Chart  3 is the presentation of the number of car chases that preceded shootings and the percentage representation of the difference between CY and PY.

Chart 4 shows the number of chases of fleeing suspects that ended in gunfire with a percentage difference between CY and PY.

Chart 5 shows the number of direct fights between police officers and suspects who did not want to retreat. Also below is the percentage difference between CY and PY.

Chart 6 shows the total number of shootings in the currently selected year, groped by the type of weapons that were in the suspect’s possession at the time of shootings.

Chart 7 represents the monthly trend of shootings and a comparison between the selected year and the previous year. 

Chart 8 shows the total number of shootings in selected years grouped by race of suspects.
All abbreviations from the original data are converted based on down below graph. W to White, B to Black, H to Hispanic, A to Asian, N to Native, and O and blanks data are under Unknown. We have 1460 unknown values regarding race of suspect.

Chart 9 represents the total number of shootings in selected years grouped by gender of suspects.

Chart 10 shows the total number of shootings in a selected year, taking into account whether the suspect had signs of mental illness or not. 

Chart 11 presents the number of shootings in a selected year based on the location (USA state) in which shootings occurred. 