---
layout: post
title: Using Custom Markers on Leaflet's Map
---

Ok, today we are going to cover how to use custom markers instead of the plain old default markers on the Leaflet's map. 

Isn't that exciting!!! I can't think of a better way to start celebrating the new year by learning something new! 

Ok, let's create the placeholder for the map: 

{% highlight html %}
	<div id="custom_map"> </div> 
{% endhighlight %}

Remember to always have Leaflet's JS and CSS files. (yeah, yeah, yeah, I know - boring reminder but hey, you need them!)

{% highlight html %}

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/leaflet/0.7.3/leaflet.css">
<script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet/0.7.3/leaflet.js"></script>

{% endhighlight %}

Remember to initialize the map and set its intial coordinates and tiles. 

{% highlight javascript %}
	var map = L.map('map').setView([33.991099, -118.466901], 9)

maplink = L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png', {
			attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'
		}).addTo(map_custom);
{% endhighlight %}

This is optional if you want to disable mouse scrolling the map which I do since it can be annoying! If you want other options, check out <a href="http://leafletjs.com/reference.html">Leaflet's API page.</a>
{% highlight javascript %}
		map_custom.scrollWheelZoom.disable();
{% endhighlight %}


Add the code beneath, and you're done!  As you can see, I chose a few of my favorite coffeeshops around in Los Angeles, and used the custom coffee marker to highlight the coffeeshops. Those coffeeshops are awesome! Try them! =) 

{% highlight javascript %}
var cIcon = L.Icon.extend({
			options: {
				iconSize:[35,42]
			}
		});

		var coffeeIcon = new cIcon({iconUrl: 'http://whimsicalhope.com/images/cute_coffee_cup.png'});

		var marker = L.marker([33.991099, -118.466901], {icon:coffeeIcon}).bindPopup("Intelligentsia").addTo(map_custom); 

		var marker = L.marker([34.038585, -118.441815], {icon:coffeeIcon}).bindPopup("Balconi Coffee").addTo(map_custom); 

		var marker = L.marker([34.093160, -118.378335], {icon:coffeeIcon}).bindPopup("Alfred Coffee").addTo(map_custom);

{% endhighlight %}


<style type='text/css'>
	#custom_map {
			width: 720px;
			height:250px;
		}
</style> 

<div id="custom_map">

</div> 

<script>
		var map_custom = L.map('custom_map').setView([33.991099, -118.466901], 10)

		maplink = L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png', {
			attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'
		}).addTo(map_custom);

		map_custom.scrollWheelZoom.disable();

		var cIcon = L.Icon.extend({
			options: {
				iconSize:[35,42]
			}
		});

		var coffeeIcon = new cIcon({iconUrl: '../images/cute_coffee_cup.png'});

		var marker = L.marker([33.991099, -118.466901], {icon:coffeeIcon}).bindPopup("<a href='http://www.intelligentsiacoffee.com/'>Intelligentsia</a>").addTo(map_custom); 

		var marker = L.marker([34.038585, -118.441815], {icon:coffeeIcon}).bindPopup("<a href='http://www.balconicoffeecompany.com/'>Balconi Coffee</a>").addTo(map_custom); 

		var marker = L.marker([34.093160, -118.378335], {icon:coffeeIcon}).bindPopup("<a href='http://www.alfredcoffee.com/'>Alfred Coffee</a>").addTo(map_custom); 

</script>
