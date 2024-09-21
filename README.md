# Covid-19 Cases, Household Income, Rental Inventory Visualization

## Data Interaction Walkthrough
The following are gifs which provide a walkthrough for interacting with data:
</br>
 
**COVID-19 Cases Over Time**</br>
Here is walkthrough interacting with the Covid-Dashboard:
</br>
<img src = 'DataVis Walkthrough/CovidDataOverTime.gif' title='COVID-19 Cases Over Time Dashboard Walkthrough' width ='' alt='Gif of walkthrough for COVID-19 Cases Over Time dashboard'/>
</br>

**Median Household Income and COVID-19 Cases by Community District**</br>
Here is a walkthrough interacting with the Median-Covid-Dashboard:
</br>
<img src = 'DataVis Walkthrough/MedianCovid.gif' title='Median Household Income and COVID-19 Cases by Community District Dashboard' width ='' alt='Gif of walkthrough for Median-Covid-Dashboard'/>
</br>

**COVID-19 Cases Over Time**</br>
Here is walkthrough interacting with the Rental-Covid-Dashboard:
</br>
<img src = 'DataVis Walkthrough/RentalCovid.gif' title='Rental Inventory and COVID-19 Cases by Community District Dashboard' width ='' alt='Gif of walkthrough for Rental-Covid-Dashboard'/>
</br>

## Visualizations
Below is a list of visualizations included in our final project along with the steps on how to recreate them yourself using Tableau after importing the data:

**Interactive map showing COVID-19 data over time as well as NYC community districts**

1.Drag the "geometry" geographical role located in the "geo_export_af59be5b-5d5a-4b31-8c85-062ea3c14f2b.shp" file onto the "detail" mark to outline NYC's community districts.

2.Drag the "Community District1" string role onto the "detail" mark to detail the community districts on the map.

3.Drag the "Case Count" number role onto the "color" mark to add the total amount of COVID-19 cases on the map. (Feel free to change the color and range by selecting "color" in the dropdown menu in the top right of the color legend.

4.Drag the "Covid Date" date role onto the "filters" card and then select relative date. After that click the special box and then click on Non-null dates. This is important for our "Covid Date Parameter" in order for it to not show areas with no dates associated such as parks and non-residential areas.

5.Right click on the "Covid Date Parameter" and select show parameter in order to enable the date selection drop down menu.

**Line graph showing COVID-19 in NYC over time**

1.Drag the "Count Date" date role into the columns field and then right click on the "year(Count Date) field in the columns and select the "Day" that is formated like so: Month, Day Year

2.Drag the "Case Count" number role into the rows field

3.Drag the "Covid Location" string role calculation into the filters card and then click on true

4.Right click on the "Location Parameter" and click on show parameter to enable the community district selection drop down menu.

**Geometric map showing Median Household Income and COVID-19 cases**

1.Drag "Geometry" from the “geo_export_af59be5b-5d5a-4b31-8c85-062ea3c14f2b.shp” file onto the "Detail" of all marks tab.

2.Drag "SUM(Case Count)" from the "COVID19 Data" file onto the "Detail" of all marks tab.

3.Drag "SUM(Median Household Income)" onto the "Color" mark under the "Latitude(generated)" mark tab. This contains median household income data.

4.Drag "SUM(Median Household Income)" onto the "Detail" mark and drag "SUM(Case Count)" onto the "Color" mark under "Latitude(generated)" 2 mark tab. This contains median household income and case count data.

Location filter:

Drag "Location" onto "Filters" field from tables. It shows neighborhood names on the map.
Covid Date filter:

IF  [Count Date]=[Covid Date Parameter] THEN [Count Date] END

If the count date is equal to the covid date parameter selected then show data for count date.

Action(Location) filter:

Go to Location under Median-Household-Income tab and click on location. Go to create and then select set and under General tab select "Use All" and apply. This filters what community districts are actionable.

SUM(Case Count) filter:

Drag "Case Count" onto "Filters" field from tables. It shows Case Count on the map. All values should be applied under Special tab.

Covid Date Parameter:

Go to "Parameters" tab and click on "Show Parameter" for "Covid Date Parameter" to enable a drop down menu to select dates.

Location Parameter:

Go to "Parameters" tab and click on "Show parameter" for "Location Parameter" to enable a drop down menu to select community districts.

**Dual-Axis graph of NYC Median Household Income and COVID-19 Cases**

1.Drag "Measure Names" from the "rentalinventory_All" file onto the "Detail" of all marks tab.

2.Drag "SUM(Median Household Income)" onto the "Detail" mark and drag "SUM(Case Count)" onto the "Detail" mark under the "SUM(Median Household Income)" mark tab. This contains median household income and case count data.

3.Drag "SUM(Median Household Income)" onto the "Detail" mark and drag "SUM(Case Count)" onto the "Detail" mark under the "SUM(Case Count)" mark tab. This contains median household income and case count data.

4.Drag "SUM(Median Household Income)" and "SUM(Case Count)" onto the rows field

5.Drag "Location" Onto the columns field

Location filter:

Drag "Location" onto "Filters" field from tables. It shows neighborhood names on the graph.

Covid Date filter:

IF  [Count Date]=[Covid Date Parameter] THEN [Count Date] END

If the count date is equal to the covid date parameter selected then show data for count date.

SUM(Median Household Income) filter:

Drag "Median Household Income" onto "Filters" field from tables. It shows Median Household Income on the graph. Non-null values should be applied under Special tab.

Covid Date Parameter:

Go to parameters tab and click on show parameter for Covid Date Parameter to enable a drop down menu to select dates.

**Line graph of NYC Rental Inventory and COVID-19 Cases**

1.Measure names from rentaliinventory_All should be used as a mark. 

2."SUM(Rental Inventory)" and "SUM(Case Count)" should be dragged into the rows field

3."DAY(RENTAL/Covid Data Single Combined)" should be dragged into the columns field

Calculation 3 filter:

IF [Community District (rentalInventory!All)] = [Location Parameter] THEN 'true' ELSEIF  [Location Parameter] = 'All' THEN 'true' END

This filter should be dragged to the filters field and be set to true.
If the community district from the data is equal to the location on the location parameter it returns true.
If the location parameter is equal to ALL it returns all data of neighborhoods and covid data on a graph.
By setting to true, data for specific locations will show up and not other locations. Other locations and ALL will return false.

**Map of Rental Inventory and COVID-19 cases**

1.Geometry from the “geo_export_af59be5b-5d5a-4b31-8c85-062ea3c14f2b.shp” shape file should be set as a mark.

2."DAY(Count Date)" should be set as a mark along with SUM(Case Count) under the "Latittude(generated)" mark. This contains COVID-19 data.

3."SUM(Rental Inventory") should be set as a mark along with DAY(Rent Date) under "Latitude(generated)2" mark. This contains rental inventory data.

4."Longitude (generated" should be put in the columns field

5. There should be two "Latitude (generated" tables int the rows field. One should contain COVID-19 data(see 2) and the other should contain rental inventory data (see 3).

Location filter: 

Dragged from tables itself. It shows neighborhood names on the map. 
Null should be excluded from the filter in order to only show non-null values.

Combined Date Parameter: 

IF  [Count Date]=[Combined Parameter] AND [Rent Date] = [Combined Parameter] THEN [Count Date] END

This parameter should be dragged to the filters field.
Uses dates from "Combined Parameter", which is made up of dates from the first of every month starting from April and ending in September
