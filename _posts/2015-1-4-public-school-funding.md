---
layout: post
title: Public School Expenditures
excerpt: "A map of Census data showing every US school district and the amount of funding that goes to their students."
modified: 2015-1-5
tags: [aaron dennis, mapbox, schools, cartography]
comments: true
image:
  feature: 
  credit: 
  creditlink: 
---
It's clear from the data below that some parts of the United States value education more than others, and it seems some students are likely significantly disadvantaged by the amount of resources they have. The data comes from the US Census Bureau. The points represent centroids of school district polygons and are styled to show the number of students in the district through size and the spending for each of those students by color. This map was built using a little bit of QGIS, R Studio, csv2geojson, and Mapbox Studio. The points are rendered on AJ Ashton's Pencil Map. You can find my processed data <a href="https://raw.githubusercontent.com/aaronpdennis/public-school-finances/master/school-district-data-small.csv">here</a>, and a larger version with more financial information <a href="https://raw.githubusercontent.com/aaronpdennis/public-school-finances/master/school-district-data.csv">here</a>.

<figure>
  <img src="/images/schools-legend.png" />
	<iframe width="100%" height="400px" frameBorder="0" src="https://a.tiles.mapbox.com/v4/aarondennis.51954ab2.html?access_token=pk.eyJ1IjoiYWFyb25kZW5uaXMiLCJhIjoiem5LLURoYyJ9.T3tswGTI5ve8_wE-a02cMw"></iframe>
	<figcaption>Expenditures per student in US school districts. <a href="http://aaronpdennis.github.io/public-schools-map/index.html">Full Map Here.</a></figcaption>
</figure>

The color scheme here is worth mentioning. Conventionally, we think of darker colors as representing higher values, and here, they do. But with a light background, lower value school districts have necessarily lower contrast and are therefore less noticeable. To solve this issue, I gave low values highly saturated colors. Looking at the legend, high values have the darkest and least saturated colors and low values have the lightest and most saturated colors. This keeps all values distinguishable and easily quantifiable and allowed me to pursue a hue change from red to blue.