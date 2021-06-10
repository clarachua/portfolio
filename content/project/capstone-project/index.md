---
date: "2021-04-27T00:00:00Z"
external_link: ""
share: true
image:
  preview_only: true
  caption: Airbnb Listings in SG by room type
  focal_point: Smart
profile: false
weight: 10

title: Geospatial Analysis of Airbnb in Singapore
summary: Project page featuring elements of my capstone project including EDA, Spatial Point Pattern Analysis and GWR.
tags:
- R-projects
- Geospatial Analysis
toc: true

links:
- name: "EDA"
  url: "https://rpubs.com/clarachua/airbnbEDA"
- name: "SPPA"
  url: "https://rpubs.com/clarachua/airbnbSPPA"
- name: "GWR"
  url: "https://rpubs.com/clarachua/airbnbGWR"
- name: "Parallelization"
  url: "https://rpubs.com/clarachua/airbnbA1"
# - icon: twitter
#   icon_pack: fab
#   name: Follow
#   url: https://twitter.com/georgecushen
url_code: ''
url_dataset: ''
url_pdf: ''
url_poster: 'files/IS612-MITB_Capstone_Project-Poster-v1.pdf'
url_project: ""
url_slides: ''
url_source: ''
url_video: ''
# slides: example
---

<!--{{% toc %}} -->

### About the Project
This page summarizes my Masters capstone project and shares the RMarkdown documents.

The motivation for this project is to specifically explore Airbnb in the Singapore market to understand the spatial distribution of Airbnb accommodation in Singapore and see how it correlates with various spatial factors in Singapore. Further analysis could also inform future policy and regulatory frameworks on short term accommodation.

The project will look at geospatial analysis to explore and explain the data around Airbnb rentals in Singapore. Namely the project aims to:

- Understand the supply of Airbnb listings from a geographical standpoint
- Determine if there are any spatial clustering of Airbnb listings
- Develop a hedonic pricing model to explain factors affecting rental pricing of the Airbnb properties

### [1. Exploratory Data Analysis (EDA)](https://rpubs.com/clarachua/airbnbEDA)
This section looks at the project motivations and literature review of studies involving spatial distributions of Airbnb listings and its impact, and Asian based studies for Airbnb.  It then explores the data available from InsideAirbnb, to look at potential insights and hypotheses about Airbnb in Singapore. 

### [2. Spatial Point Pattern Analysis](https://rpubs.com/clarachua/airbnbSPPA)
This section looks at potential spatial clustering of Airbnb in Singapore using Spatial Point Pattern Analysis using the K-Function tests.  It also provides a discussion of different techniques to obtain the results for larger datasets.  

#### [K-Function Test Computation](https://rpubs.com/clarachua/airbnbA1)
This shows the computation of SPPA K-Function Tests by Subregions and Room Type, and the use of parallelisation to compute larger datasets and functional programming (using purrr) for more efficient programming methods.  

### [3. Geographically Weighted Regression (GWR)](https://rpubs.com/clarachua/airbnbGWR)
This section looks at the literature review of studies involving hedonic pricing research in the context of Airbnb.  It then examines the hedonic pricing of Airbnb listings in Singapore, using a geographically weighted regression (GWR). 

Understanding the hedonic price of Airbnb listings would help to provide hosts or would be hosts with insights on how to price their listing, and also help researchers and policy makers trying to understand how Airbnb pricing may impact adjacent areas such as hotel revenues, pricing of long-term rentals and the housing market, as well as impact on gentrification of neighbourhoods.

#### [Data Collation and Wrangling for GWR](https://rpubs.com/clarachua/airbnbA2)
This section shows the data collation and wrangling of hypothesized pricing determinants:
- Listings location
- MRT train station exits
- Hotel locations
- Healthcare facilities
- Shopping malls
- Categorical variables (Superhost, Room types, Cancellation policies)

#### [GWR Bandwidth & Model Selection](https://rpubs.com/clarachua/airbnbA3)
This section shows the code for determining the bandwidth and model selection for the basic GWR.  
