---
layout: post 
title: Creating a Popup on Leaflet's Map 
---
This is a small tutorial on creating a popup on a Leaflet's map.

[Leaflet](http://leafletjs.com/) is an awesome open-source javascript library map. 

First, create a Leaflet's map with longitude and latitude at a place of your own picking. You can obtain longitude and latitude of any place by putting their address in a site that "translates" the address into long/lat coordinates. Just google for any random one. 

My coordinates are of one of my favorite coffeeshops here at LA, Demitasse Cafe. 

The steps beneath are similar to the ones given at Leaflet's site. 

{% highlight javascript %}
var map = L.map('map').setView([34.049774, -118.241710], 17); 
{% endhighlight %}

Then add this: 

{% highlight javascript %}

mapLink =
'<a href="http://openstreetmap.org">OpenStreetMap</a>'; L.tileLayer(
'http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', { attribution: 'Map data &copy; ' + mapLink, maxZoom: 18, }).addTo(map);
{% endhighlight %}

Make sure to have this, otherwise, the map has no place to show up! 

{% highlight html %}

<div id='map'>
		
</div>

{% endhighlight %}

And here is its CSS: 

{% highlight CSS %}
   #map {
      width:720px;
      height:400px;
   }
 {% endhighlight %}

This is the popup! You can customize easily. 

{% highlight javascript %}
var marker = L.marker([34.063298, -118.260126]) .addTo(map).bindPopup("<b><a href='http://cafedemitasse.com/'>Demitasse Cafe!</a></b><br />").openPopup();
{% endhighlight %}

<div id='map'>
		
</div>

<style type="text/css">
      #map {
        width:720px;
        height:250px;
              }
</style>

<script>

var map = L.map('map').setView([34.049774, -118.241710], 17); 

mapLink =
'<a href="http://openstreetmap.org">OpenStreetMap</a>'; L.tileLayer(
'http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', { attribution: 'Map data &copy; ' + mapLink, maxZoom: 18, }).addTo(map);
			

var marker = L.marker([34.049774, -118.241710]).addTo(map).bindPopup("<b><a href='http://cafedemitasse.com/'>Demitasse Cafe!</a></b><br />").openPopup();


</script>

To sum up: this is all the code that was used to create this map and its popup. 

{% highlight javascript %}

<script>

var map = L.map('map').setView([34.049774, -118.241710], 17); 

mapLink =
'<a href="http://openstreetmap.org">OpenStreetMap</a>'; L.tileLayer(
'http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', { attribution: 'Map data &copy; ' + mapLink, maxZoom: 18, }).addTo(map);
			

var marker = L.marker([34.049774, -118.241710]).addTo(map).bindPopup("<b><a href='http://cafedemitasse.com/'>Demitasse Cafe!</a></b><br />").openPopup();


</script>



{% endhighlight %}

Be sure to also include Leaflet's JS and CSS files, otherwise the code here won't work. =) 

If you don't want to download Leaflet's JS and CSS files, you can use the public CDNs available. 

{% highlight html %}

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/leaflet/0.7.3/leaflet.css">
<script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet/0.7.3/leaflet.js"></script>

{% endhighlight %}

And, that's it! 
