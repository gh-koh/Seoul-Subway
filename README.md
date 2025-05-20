# Seoul Subway Project

Data analysis and visualization of [Seoul Metropolitan Subway](https://en.wikipedia.org/wiki/Seoul_Metropolitan_Subway) traffic

## Overview

The Seoul Metropolitan Government makes large amount of data available on the [Seoul Open Data Plaza](https://data.seoul.go.kr/). Monthly data on the number of passengers who get on/off at each station is available [here](https://data.seoul.go.kr/dataList/OA-12252/S/1/datasetView.do). The data is provided in the form of total passengers per month for each hourly interval, e.g. 650 passengers got on 동대문역 (Dongdaemun station) between 0400 and 0500 for the month of April in 2025, so an average of 22 passengers got on that station between 0400 and 0500 every day. A dataset with information on each station, along with its coordinates, is also available [here](https://data.seoul.go.kr/dataList/OA-21232/S/1/datasetView.do). By scraping HTML data from a [map](http://www.seoulmetro.co.kr/kr/cyberStation.do) of the subway system, we can generate a graph of the subway system and visualize it, with the nodes as stations and edges as lines. In addition to being able to visualize it in an intuitive form as a graph, such a transformation allows us to easily perform analysis on the system.

## Notes
 - Although the traffic data contains data for all 24 hours, the subway usually starts running after 0500 and ends running before 0100, so 0100 ~ 0500 was excluded from the visualization and analysis.
 - Due to the way the data was cleaned, the time lapse of the system does not reflect changes in station names (e.g. 지제역 (Jije station) &#8594; 평택지제역 (PyeongtaekJije station)).
 - Many lines and stations (such as the entirety of the Incheon Lines 1 and 2) were not included in the scope of the traffic dataset and were thus also excluded from the visualization; hence the visualization shown here does not represent the entirety of the network.
 - The traffic dataset does not provide information on the flow of passengers (i.e. how much of the total passengers who get on a station head to which of the neighboring stations) and moreover, stations connected to more than one line (transfer stations) also don't breakdown passenger information into lines (i.e. how much of the total passengers who get on a transfer station use which line) so the original idea of converting the subway system into a symmetric directed graph had to be scrapped in favor of just a simple graph.

## Ideas for extensions, improvements
 - Streamline data cleaning process, eliminate unnecessary objects and steps
 - Implement an interactive map so that the user can select specific timeframes to visualize
 - ML to predict future traffic?
    - Possible complication: planned changes to subway system, population changes
 - Use the OpenAPI feature to automatically access traffic data
 - Get accurate daily average for each month instead of merely dividing by 30
 - English translations for lines, stations (scrape from OSM?) (nvm, there is an English version of the map in the site...)
 - Analyze data using graph-theoretic functions as only constructed graph in Networkx, turned out visualization didn't need Networkx

 ## Sample image for 2025-02