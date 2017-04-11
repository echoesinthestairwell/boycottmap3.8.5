# boycottmap3.8.5
update from 3.8.2:
changed the base map from osm to stamen toner-lite - http://maps.stamen.com/toner-lite/

purpose of the map: To depict signatories with an academic affiliation on a petition calling for a boycott of academic conferences in the US in response to the Trump Administration's discriminatory travel ban from, first 7, now 6, Muslim-majority countries.

summary: The map depicts ~5389 signatories, affiliated with 1065 institutions, in 86 countries. it also depicts states/provinces for the US, Canada,and Australia, subnational units for the United Kingdom and Israel/Palestine. Disputed territories are largely the default of Natural Earth, the presence or absence of particular territories being marked disputed is not a statement by the author on competing territorial claims. The exception is Kashmir.

source of data: This map was created using data from an online petition here: https://docs.google.com/forms/d/e/1FAIpQLSeNN_2HHREt1h-dm_CgWpFHw8NDPGLCkOwB4lLRFtKFJqI25w/viewform?c=0&w=1&fbzx=2104368019732744200 The data is current as of 2017.03.10.

cleaning data: I just copied and pasted the signatures into a csv and proceeded to clean the data by hand. This was time consuming given that there was no standardized format for entering signatures. Once I had separated names from institutions I ran the file through a geocoding api and sorted results to standardize institution names. For all but the last 87 signatories, the results were then reverse geocoded to get standardized names for the institutions being coded.

Some signatures identified no institutional affiliation. Some were duplicates. Some used acronyms that proved too ambiguous to geocode, as the enginewould erroneously default to the wrong part of the world. I was able to resolve some of these laboriously line by line; others were excluded only for the sake of time. I also excluded institutions like hospitals without a clear academic reference. In the end, I had ~5389 signatures out of ~5755 original entries.

extracting summary data: Not yet conversant with PostGIS and VPSs, I ran the resulting files through python codes to generate dictionaries and counts of institutions and geographic units like countries and provinces.

producing the map: The map was produced using QGIS 2.18.2. The shapefiles are from Natural Earth, medium scale, cultural: http://www.naturalearthdata.com/downloads/ The webmap was produced using the leaflet2web plugin. https://github.com/tomchadwin/qgis2web Much thanks to the coders for producing this! The base layer tiles are from Stamen.
