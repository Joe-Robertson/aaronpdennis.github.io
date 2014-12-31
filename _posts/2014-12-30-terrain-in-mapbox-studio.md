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
Mapbox Studio provides access to vector hillshades for styling maps with terrain. The <a href="https://www.mapbox.com/blog/mapbox-terrain-data-update/">most recent global vector terrain dataset</a>, Mapbox Terrain Version 2, is designed to provide "twice as much shadow detail and is based on a combined hill-shading and slope-shading technique that allows for better emphasis in areas of steep terrain." This looks great on the big mountains, but it comes at the small sacrifice of detail on softer landscapes. 

In the maps below, terrain with Version 1 reveals rolling hills in the valleys between ridges. Mapbox Terrain Version 2 provides sharp detail along the ridges, but seems to flatten the valleys.

<figure>
	<img src="/images/mapbox-terrain/ridge-valley-v1.png">
	<figcaption>Mapbox Terrain V1</figcaption>
</figure>

<figure>
	<img src="/images/mapbox-terrain/ridge-valley-v2.png">
	<figcaption>Mapbox Terrain V2</figcaption>
</figure>

Each terrain version has its strengths. A workaround that realizes the benefits of both is to reference `mapbox.mapbox-terrain-v1,mapbox.mapbox-terrain-v2` as sources for your Mapbox Studio project. This allows you to render both as layers on your map.

<figure>
	<img src="/images/mapbox-terrain/ridge-valley-v1v2.png">
	<figcaption>Mapbox Terrain V1 & V2</figcaption>
</figure>

The issue here is that `#hillshade` will reference two different layers. V1's four classes of hillshade polygons can be identified uniquely as either `full_highlight`, `medium_highlight`, `medium_shadow`, or `full_shadow`. V2 terrain has six unique levels of lightness. If you're looking to inlcude `#contour` or `#landcover`, this method will result in each version rendering on the map, causing confusing overlap. V2 will have more detailed versions of these layers than V1, and is probably the better choice. However, if you're only interested in a hillshade on your map, you might consider using both.

<figure>
	<iframe width="100%" height="500px" frameBorder="0" src="https://a.tiles.mapbox.com/v4/aarondennis.670c48aa.html?access_token=pk.eyJ1IjoiYWFyb25kZW5uaXMiLCJhIjoiem5LLURoYyJ9.T3tswGTI5ve8_wE-a02cMw"></iframe>
	<figcaption>Incorporating both versions of Mapbox Terrain</figcaption>
</figure>

The CartoCSS used to style the terrain hillshades in the map above:

<pre><code class="CSS">#hillshade {
  [class='full_shadow'] {
    polygon-fill: #202020;
    polygon-opacity: 0.1;
  }
  [class='medium_shadow'] {
    polygon-fill: #464646;
    polygon-opacity: 0.05;
  }
  [class='medium_highlight'] {
    polygon-fill: #fff;
    polygon-opacity: 0.05;
  }
  [class='full_highlight'] {
    polygon-fill: #fff;
    polygon-opacity: 0.2;
  }
  
  [level=94] { 
    polygon-opacity: 0.1; 
    polygon-fill: #fff; 
  }
  [level=90] { 
    polygon-opacity: 0.1; 
    polygon-fill: #939393; 
  }
  [level=89] { 
    polygon-opacity: 0.13; 
    polygon-fill: #4f4f4f; 
  }
  [level=78] { 
    polygon-opacity: 0.15; 
    polygon-fill: #3b3b3b; 
  }
  [level=67] { 
    polygon-opacity: 0.175; 
    polygon-fill: #171717; 
  }
  [level=56] { 
    polygon-opacity: 0.2; 
    polygon-fill: #000000; 
  }
  comp-op: hard-light;
}
</code></pre>