#Using QGIS Styles with OpenStreetMap Data

This tutorial will show how to download an Open Street Map (OSM) .pbf file (compressed spatial data format), load it into a SQLite database, and style it using QGIS style files.

###Download OSM Data###

First, start by downloading the area you're located from the GeoFabrik website:

 [http://download.geofabrik.de/north-america.html](http://download.geofabrik.de/north-america.html)

The result is a file with a .osm.pbf extension. We use the Colorado file, our file is called colorado-latest.osm.pbf

At this point, the file - which is huge - can have the Google-like styles applied, but we'll clip it to a bounding box of the Denver area, and convert it to a SQLite file.

###Import into SQLite###

With GDAL installed, you can use the ogr2ogr command to both clip and load the downloaded file in one command.

Next, using using terminal or command prompt, navigate to the directory you downloaded your

To download the entire State, use this syntax:

	ogr2ogr -f "SQLite" -dsco SPATIALITE=YES Denver_OSM colorado.osm.pbf
 
And to limit the area you want to import to a specific bounding box, use this syntax:

	ogr2ogr -f "SQLite" -dsco SPATIALITE=YES -spat -105.1457194640948671 39.4826335795378611 -104.5138338857370286 39.9707611278579904 Denver_OSM colorado.osm.pbf


Thanks to [Anita Graser](http://anitagraser.com/2014/05/31/a-guide-to-googlemaps-like-maps-with-osm-in-qgis/) for first publishing these instructions.

