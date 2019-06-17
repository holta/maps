## Offline OpenStreetMap + Regional Vector Map Datasets

### How do I add Zoomable Maps for my region?

Make sure you have [Internet-in-a-Box](http://internet-in-a-box.org) (IIAB) [7.0](https://github.com/iiab/iiab/wiki/IIAB-7.0-Release-Notes) (or higher) installed.

Use its Admin Console (http://box.lan/admin, default passwords at http://FAQ.IIAB.IO) to click Install Content (on top) > Get Map Region (on the left).

Pick a checkbox on the left to download, unpack and install the Map Region (Map Pack) you want.  As you mouse over the choices on the left, colorful bounding boxes light up on the world map on the right, to help you choose the Map Pack most suitable for your region.

As of June 2019 you can choose among the major continents, Central America (3.77 GB), the Middle East (7.66 GB) or the World (53.17 GB).  A working example/sample of the latest maps in action can generally be previewed at: http://iiab.me/maps

After making your choice, kick off your Map Pack download/installation using the 'Install Selected Region' button.

Please be patient as this can sometimes take a few hours, depending on your Internet connection etc!  You can monitor the progress by clicking Utilities (on top) > Display Job Status (on the left).

Once this is complete, try it out at http://box/maps &mdash; and also look over your new IIAB home page (typically http://box, or http://172.18.96.1, or http://box.local) where a new Content Pack should appear, briefly describing the Map Pack you installed &mdash; for students and teachers to click on!

#### SEE ALSO

["How do I add zoomable maps for my region?"](http://FAQ.IIAB.IO#How_do_I_add_zoomable_maps_for_my_region.3F) in [FAQ.IIAB.IO](http://FAQ.IIAB.IO)

### History And Architecture

1. OpenMapTiles.com has published a 2017-07-03 version of OpenStreetMap (OSM) data and converted it into [MVT](https://www.mapbox.com/vector-tiles/) Mapbox Vector Tile format, for many dozens of regions around the world.  (This is an [open standard](https://www.mapbox.com/vector-tiles/specification/) which puts all of a region's vector tiles into a single SQLite database, in this case serialized as [PBF](https://wiki.openstreetmap.org/wiki/PBF_Format) and then delivered in a single .mbtiles file.)
1. https://s2maps.eu/ has made free satellite images to zoom level 13 (20M per  pixel) available. These are combined with the OSM data in Internet-in-a-Box (IIAB) maps. These two sources create highly zoomable regional vector map datasets &mdash; each such .mbtiles file has a very minimal footprint &mdash; yet displays exceptional geographic detail.  IIAB's space-constrained microSD cards (typically running in a Raspberry Pi) greatly benefit!
1. Thankfully the [MBTiles](https://github.com/mapbox/mbtiles-spec) file format can be used to store either bitmap/raster tilesets or vector tilesets.  So 3 essential data files are needed = 1 city search database + 2 .mbtiles files, one each for OSM and Satellite data:
   1. cities1000.sqlite (25 MB) so users can search for and locate any of 127,654 cities/settlements worldwide, whose population is larger than 1000.
   1. The world's landmasses are covered by `detail.mbtiles -> <regional selection of OSM data>.mbtiles` (2-10GB depending on region) at zoom levels 0-18, encoded as MVT/PBF vector maps.
   1. Satellite imagery of the World  covered 'satellite.mbtiles -> satellite_z0-z9.v3.mbtiles` (932 MB) at zoom levels 0-9, encoded as JPEG bitmap/raster imagery.
 

Code:
  - [github.com/iiab/maps](https://github.com/iiab/maps) is the source for IIAB maps.

Design Decisions:
  - [github.com/iiab/iiab-factory/blob/master/content/vector-tiles/Design-Decisions.md](https://github.com/iiab/iiab-factory/blob/master/content/vector-tiles/Design-Decisions.md)
  - [github.com/georgejhunt/iiab-factory/blob/vector-maps/content/vector-tiles/Design-Decisions.md](https://github.com/georgejhunt/iiab-factory/blob/vector-maps/content/vector-tiles/Design-Decisions.md) just in case!

Usability Engineering begins here &mdash; thanks all who can assist &mdash; improving this for schools worldwide!
  - ~Teachers want Accents to work when searching for cities in OpenStreetMap [#662](https://github.com/iiab/iiab/issues/662)~ (Can multilingual folk confirm this is really/sufficiently fixed?)

_How do we evolve this into a continuously more friendly product?_
