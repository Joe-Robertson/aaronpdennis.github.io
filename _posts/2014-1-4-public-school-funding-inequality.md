---
layout: post
title: Public School Expenditures
excerpt: "A map of Census data showing every US school district and the amount of funding that goes to their students."
modified: 2014-12-30
tags: [aaron dennis, mapbox, schools, cartography]
comments: true
image:
  feature: 
  credit: 
  creditlink: 
---
It's clear from the data below that some parts of the United States value education more than others, and it seems some students are likely significantly disadvantaged by the amount of resources they have. The data comes from the US Census Bureau. The points represent centroids of school district polygons and are styled to show the number of students in the district through size and the spending for each of those students by color. This map was built using QGIS, csv2geojson, and Mapbox Studio. You can find my processed data <a href="https://raw.githubusercontent.com/aaronpdennis/public-school-finances/master/school-district-data-small.csv">here</a>, and a larger version with more financial information <a href="https://raw.githubusercontent.com/aaronpdennis/public-school-finances/master/school-district-data.csv">here</a>.

<figure>
  <img src="images/schools-legend.png" />
	<iframe width="100%" height="550px" frameBorder="0" src="https://a.tiles.mapbox.com/v4/aarondennis.a3832b50.html?access_token=pk.eyJ1IjoiYWFyb25kZW5uaXMiLCJhIjoiem5LLURoYyJ9.T3tswGTI5ve8_wE-a02cMw"></iframe>
	<figcaption>Expenditures per student in US school districts. <a href="https://api.tiles.mapbox.com/v4/aarondennis.a3832b50/page.html?access_token=pk.eyJ1IjoiYWFyb25kZW5uaXMiLCJhIjoiem5LLURoYyJ9.T3tswGTI5ve8_wE-a02cMw#5/37.370/-83.298">Full Map Here.</a></figcaption>
</figure>