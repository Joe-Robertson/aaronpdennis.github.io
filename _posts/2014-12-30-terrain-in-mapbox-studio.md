---
layout: post
title: Terrain in Mapbox Studio
excerpt: "A look at Mapbox Terrain Version 1 and Version 2."
modified: 2014-12-30
tags: [aaron dennis, mapbox, terrain, cartography]
comments: true
image:
  feature: 
  credit: 
  creditlink: 
---
Mapbox Studio provides access to vector hillshades for styling maps with terrain. The most recent global vector terrain dataset, Version 2, uses incredibly high resolution elevation data and is designed to provide "twice as much shadow detail and is based on a combined hill-shading and slope-shading technique that allows for better emphasis in areas of steep terrain." This looks great on the big mountains, but it comes at the small sacrifice of detail on softer landscapes. 

In the images below, Version 1 reveals rolling hills in the valleys while Version 2 provides sharp detail along the ridges, but seems to flatten the valleys.

<figure>
	<img src="/images/mapbox-terrain/ridge-valley-v1.png">
	<figcaption>Mapbox Terrain V1</figcaption>
</figure>

<figure>
	<img src="/images/mapbox-terrain/ridge-valley-v2.png">
	<figcaption>Mapbox Terrain V2</figcaption>
</figure>

Both terrain versions have their strengths. A workaround that realizes the benefits of both is to reference both `mapbox.mapbox-terrain-v1,mapbox.mapbox-terrain-v2` as sources for your Mapbox Studio project.

<figure>
	<img src="/images/mapbox-terrain/ridge-valley-v1v2.png">
	<figcaption>Mapbox Terrain V1 & V2</figcaption>
</figure>

The issue here is that `#hillshade` will reference two different layers. V1's four classes of hillshade polygons can be identified uniquely as either `full_highlight`, `medium_highlight`, `medium_shadow`, or `full_shadow`. V2 terrain has six unique levels of lightness. If you're looking to inlcue `#contour` or `#landcover`, this method will result in each version rendering on the map, causing confusing overlap. V2 will have more detailed versions of these layers than V1.