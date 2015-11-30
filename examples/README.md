Mapbox Integration Example
=========

Here below a good starting point for testing the vector tiles created by Tilemaker with [Mapbox compatible process lua file](https://github.com/Innovisite/tilemaker/blob/master/resources/mbx_compatible_process.lua) and [Mapbox compatible configuration file](https://github.com/Innovisite/tilemaker/blob/master/resources/mbx_compatible_config.json)

Collecting OpenStreetMap data
----------

First, download a pbf OpenStreetMap dump from your favorite OSM datasource.

* [GEOFABRIK](http://download.geofabrik.de/)
* BBBike (http://extract.bbbike.org/)
..

You can also download an OpenStreetMap file in xml format from [Overpass/XAPI](http://wiki.openstreetmap.org/wiki/Downloading_data) and then convert it to pbf format thanks to converter tools such as 
[OSMOSIS](https://github.com/openstreetmap/osmosis) with the [Mapsforge Map-Writer plug-in](https://github.com/mapsforge/mapsforge/blob/master/docs/Getting-Started-Map-Writer.md).

Creating vector tiles via Tilemaker
----------

Use the [Mapbox compatible process lua file](https://github.com/Innovisite/tilemaker/blob/master/resources/mbx_compatible_process.lua) and [Mapbox compatible configuration file](https://github.com/Innovisite/tilemaker/blob/master/resources/mbx_compatible_config.json) to create the vector tiles with Tilemaker, output folder must be ** examples/tiles** as shown below:

	tilemaker <your_osm_file>.pbf --output=examples/tiles --config=resources/mbx_compatible_config.json --process=resources/mbx_compatible_process.lua 

Updating map center coordinates
----------

In order to set the initial map bounding box that fits the OSM bounding box from the data you have downloaded you will have to edit *index.html* file and more precisely *zoom* and *center* properties.
	 
	 var map = new mapboxgl.Map({
    	container: 'map',
    	style: 'examples/local-street-v8.json',
    	zoom: <YOUR_ZOOM_LEVEL>,
    	center: [YOUR_LATITUDE, YOUR_LONGITUDE]
  	});

Running
----------

Start a local webserver on port **8001** from the tilemaker folder, open a browser and enter
	
	http://localhost:8001/example

and you are done!