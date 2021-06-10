---
date: "2018-12-02T00:00:00Z"
external_link: ""
share: true
image:
  preview_only: false
  caption: Hawker Stall Rentals
  focal_point: Smart
profile: false
weight: 20

title: Visualisation & Analysis of Hawker Stall Rental Prices
summary: This project looks at a R Shiny app that allows users to explore Singapore's public hawker centre rental data (as at end 2018).  
tags:
- R-projects
- Geospatial Analysis
- Visualisation

toc: true

header:
  image: "media/1600px-G1-Cover4.jpg"
  caption: "Hawker Rentals"

links:
- name: "Shiny App"
  url: "https://clarachua.shinyapps.io/HawkerGWR/"
- name: "Original Project Page"
  url: "https://wiki.smu.edu.sg/18191isss608g1/Group01_Proposal"
url_code: ''
url_dataset: ''
url_pdf: 'files/Research_Paper_Hawker.pdf'
url_poster: 'files/G1-Hawker_Poster.jpg'
url_project: ""
url_slides: 'files/Slides_Hawker.pdf'
url_source: ''
url_video: ''
# slides: example
---

{{< toc >}}

## __About the Project__
This is a group project that was done as part of the MITB Visualiation Analytics module.  

### Overview
Hawker centres are a staple in the Singapore food scene. In July 2018, there was a bid of $10,028 monthly rental for a drinks stall at Chomp Chomp Food Centre[^1].  The hawker in question has since ended the tenancy agreement, but this has led us to wonder: do hawkers know what is the market rate for hawker stalls and do they know how much to bid? 

NEA manages and regulates 114 public hawker centres in Singapore. Every month, NEA puts up vacant stalls at various hawker centres for tender, which are then awarded to the highest bidders. Aspiring hawkers will need to submit a tender bid for a selected stall. If they are the winning bidder, they have a license to operate the stall for 3 years, after which they may need to renew or bid for a stall again. Bidders who fail to sign the Tenancy Agreement after being awarded the stall will have their deposit forfeited and be debarred from participating in all future government tenders. Therefore, it is important for bidders to know what is a ‘fair’ market rate to pay for their stall, as well as what is sustainable for their business.

[^1]: https://www.straitstimes.com/singapore/10028-monthly-rental-bid-for-chomp-chomp-hawker-stall-highest-in-3-years-bidder-walked

### Project Objectives
Although information on past rentals are publicly available on NEA’s website, it is not in a form that is easily accessible to users. Our project aims to understand hawker centre rentals by visualising the rental price trends of different hawker centres, and to analyse the factors that affect stall rentals.

Our group aims to build an app to allow users to explore Singapore’s public hawker centre rental data. Users will be able to view price trends, and lookup prices of hawker stall rentals in the selected hawker centre. Users may be able to use our app to see if their rental bid price is within the market range for the type of stalls in their desired market.

More advanced users can use our app to view a geo-weighted regression to understand how locations and different variables affect the rental price of the hawker stalls.

The variables include:
- Availability of & proximity to MRT and buses
- Availability of & proximity to car parks
- Proximity to HDB blocks as a proxy for population
- Hawker stall size and type

<br>

## __Data Source__

Our project uses data from [__published tender notices__](https://www.nea.gov.sg/corporate-functions/resources/tender-notices) on the National Environmental Agency's website as well as information retrieved various publicly available and personal sources. Special credits to Prof. Kam Tin Seong for providing us a list of geocoded HDB postal code as one of the parameters for our project.

The metadata table of our main working file is shown below:

|Column | Description | Example | Data Source |
|:--    | :---:       | :---    | :---        |
| HAWKER_CENTRE | Name of hawker centre | Amoy Street Food Centre | NEA "List Of 5 Highest Tender Bids" |
| STALL_NO | Unit number of stall | 01-66B | NEA "List Of 5 Highest Tender Bids"|
| STALL_AREA | Size of stall (sqm) | 5.65 | NEA "Tender Bids For Hawker Stalls From March 2012 To September 2018" |
| TRADE | Specific type of trade | Vegetables | NEA "List Of 5 Highest Tender Bids" |
| TRADE_GENERIC | Generic type of trade | Fresh Produce | Derived from "Trade" |
| TENDERED_BID | Successful bid price ($) | $2988 | NEA "List Of 5 Highest Tender Bids" |
| AVERAGE_BID_PRICE | Average successful bid price of Hawker Centre ($)| $450 | Derived from "Tendered bid"|
| MONTH | Month of successful  bid | Apr | NEA "Tender Bids For Hawker Stalls From March 2012 To September 2018" |
| YEAR | Year of successful  bid | 2017 | NEA "Tender Bids For Hawker Stalls From March 2012 To September 2018" |
| DATE | Month and Year of successful bid | Apr-2017 | NEA "Tender Bids For Hawker Stalls From March 2012 To September 2018" |
| TYPE_OF_STALL| Type of business | Market Stalls | NEA website |
| POSTAL CODE | 6 digit zip code representing postal location of hawker centre | 560572 | NEA website |
| LAT | Latitude in 7d.p. | 1.2793399 | Derived from postal code using R |
| LONG | Longitude in 7.d.p | 103.8466525 | Derived from postal code using R |
| BID_PRICE_PER_SQM | Tendered bid price of stall divided by stall size in sqm | 528.85 | Derived from tendered price and store size |
| LAST_RENOVATION | Reopening date after renovation | Feb-2003 | NEA Hawker Centres Upgrading Programme [https://www.nea.gov.sg/our-services/hawker-management/programmes-and-grants/hawker-centres-upgrading-programme/hup-gallery] |
| AGE_OF_HAWKER | Number of years past since reopening date| 15.8 | Derived from fraction of year since reopening date |
| TYPE_OF_UPGRADING | Reason for upgrading | Reconfiguration | NEA Hawker Centres Upgrading Programme |

<br>

## __User Guide for App__
### Interactive Map Tab
{{< figure src="media/G1-Interactive_Map_Tab.png">}} 

The interactive map tab gives a mapped overview of the location and distribution of rental price trends across different hawker centres in Singapore. Each hawker centre’s location is represented by a blue marker on the Singapore map. When the user clicks on a marker, a pop-up box will display the name of the hawker centre, the number of available cooked food stalls and market stalls. Other information displayed includes the number of bus stops, HDB blocks, HDB carparks and MRT stations within a 350m radius of the hawker centre.

__[1]__ An interactive box plot of the average bid price per sqm of all hawker centres in Singapore stall type is embedded at the top of the side tab panel. This allows users to have a visual comparison between the bid price distribution of selected hawker centres and all hawker centres in Singapore.

__[2]__ A dynamic time series line graph of average bid price per sqm of selected hawker centre is embedded as the second plot on the panel. User will be able to appreciate changes in bid prices of market and cooked food stall in the selected hawker centre over the years.

__[3]__ A dynamic box plot embedded at the bottom of the panel shows the bid price per sqm by stall type in a selected hawker centre. Unlike [1], this box plot is interactive, and updates when a different hawker centre is selected.

### Exploratory Tab
The exploratory tab contains 4 independent interactive plots to assist user in understanding the distribution of bid price and count across different types of hawker stalls and trade types in Singapore.    

##### Subtab 1: Line Graph
{{< figure src="media/G1_Visual_subtab1.png" >}} 

Sub tab 1 displays an interactive time series line graph of average bid price of market and cooked food stalls across all hawker centres. 

As the user hovers over a point on the line graph, the total number of successful bids for cooked food and market stalls for that corresponding year will be returned as a message at the top right corner of the plot.

##### Sub tab 2: Scatter plot
{{< figure src="media/G1_Visual_subtab2.png" >}} <!--caption="Age of hawker stall vs bid price per sqm" >}} -->

The scatterplot of age of hawker against bid price per sqm allows user to have an appreciation of the relationship between recency effect of renovation/ opening on rental prices.
Upon hovering across each data point, a pop-up box will return the age of hawker in years and average bid price in the following format (year since last renovation/opening, average bid price per sqm)


##### Sub tab 3: Bar & Line plot
{{< figure src="media/G1_Visual_subtab3.png" >}} <!--caption="Hawker Trade Types vs Bid counts and Average bid price" >}} --> 
Sub tab 3 showcases a dual axis bar/line chart where hawker trades are plotted against the number of successful bid counts and average bid price per sqm. Bid count of each trade is represented by the height of the bar in a bar chart and its corresponding average bid price is plotted as a line graph. 

As user hovers over each bar, the corresponding number of bid count across 2012-2018 will be reflected in a pop-up box.

Similarly, the average bid price per sqm of each individual trade will appear in a pop-up box as user hover over the line graph.

##### Sub tab 4: Treemap
{{< figure src="media/G1_Visual_subtab4.png" >}}
The interactive Treemap incorporates a hover and drill-down function. The number of successful bid counts across 2012-2018 for each trade is represented by the size of the rectangle/ square. The average price per sqm of a trade across 2012-2018 is represented by color of the rectangle/square which increases in shade as rental prices increases.

**__Hover Function__**
{{< figure src="media/G1_Visual_subtab4_hover.png" >}}
As users hover over the plot, all trades under the overarching stall types (market stall vs. cooked food stall) will be highlighted in a darker shade of blue.

__[1]__ A pop-up box will reflect the total number of successful bids for cooked food stalls across all hawker centres from 2012-2018.

**__Drill Down function__**
{{< figure src="media/G1_Visual_subtab4_drill.png" >}}
Users can click on either one of the two overarching stall types (market stall vs. cooked food stall) to zoom in to view the proportion of bid counts and bid price per sqm of all trades applicable to that stall type.

__[2]__ At the drilled-down layer, the hover function returns the total number of successful bids for the selected trade across all hawker centres from 2012-2018.

__[3]__ Users can click on the < Back icon to return to the overarching view of the treemap

### GW Regression Tab
{{< figure src="media/G1_Visual_gwr_1.png" >}}

Using the User Input Panel in the Model tab, users can select different combinations of variables to perform GW Regression and interpret the correlations through the colour gradient of the correlation plot generated. Negative correlation is represented by shades of red and positive correlation by shades of blue.

Additionally, users can perform Geographically Weighted Regression (GWR) through the selection of regression type, kernel functions, independent and dependent variables. A model comparison table shows the fit statistics of both the global linear model (LM) and GW Regression model. Once the regression is run, users can see which variables that are significant at 90%, 95%, 99% and 99.9% level.

The GWR Plot tab gives a localised coefficient and p-value for each hawker centre, and we can identify clusters of hawker centres that show similar characteristics.  Users can select the variable to explore and see how that impacts each hawker centre. There are 2 sub tabs for users to toggle between: Models and GWR Plots.

##### Sub tab 1: Models

__Components of User Inputs Panel__
{{< figure src="media/G1_Visual_gwr_sub1.png" >}}

Users may choose the parameters to input for the GW Model as follows:
- Type of stall: Cooked Food Stalls, Market Stalls
- Select Kernel: Gaussian, Exponential, Box-Car, Bo-Squared, Tri-Squared
- Dependent Variable: Average Price psm, Median Price psm
- Select Independent Variables: All, None
- Regression Type: Basic GWR, Robust GWR – Filtered, Robust GWR - Downweight

{{< figure src="media/G1_Visual_gwr_sub1_2.png" >}}
__[1]__ Significance level – After performing the GW Regression, users can see which variables are significant at 90%, 95%, 99% and 99.9% level.

__[2]__ Model Comparison – Users can compare how Geographically Weighted Regression (GW) model perform when benchmarked against the Global Linear Regression Model (LM) using the various metrics.

__[3]__ Global GW Regression Model Coefficients & p-value – Users can compare the significance of each individual inputs in the GW model

##### Sub tab 2: GWR Plot
{{< figure src="media/G1_Visual_gwr_sub2_1.png" >}}

__[1]__ Users may toggle between 21 input variables to view the coefficient and p-value bubble plots for each variable.

__[2]__ Users can download the results of the GW Regression with the following information – name of hawker centre, longitude, latitude, intercept, coefficient, actual dependent variable (y), predicted dependent variable (yhat), residual value, standard error t-value and p-value.

__[3]__ Users can select to view up to 10, 25, 50, 100 rows of data at one time.

__[4]__ Users may sort the results table according to the coefficient, p-value, actual dependent variable, predicted dependent variable and R² value.

__[5]__ Users may key in the search name.
