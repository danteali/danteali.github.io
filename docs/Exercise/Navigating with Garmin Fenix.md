---
Created:  '2021-08-18 12:03:22 +01:00'
Modified: '2021-08-18 12:03:22 +01:00'
---

| Tags: #garmin #hike #cycle #gps #gpx |
| ----- |

---

> # Key Takeaways / Things to Remember
> 

---
# Navigating with Garmin Fenix (and Forerunner)

Some Garmin watches, including the Fenix, have a 'Navigation' function which can display minimalist maps on screen during activities. It is fairly trivial to get routes onto the watch and display them.

Another mechanism is to use one of the 3rd party apps for the watches which tend to have more functionality than the Navigation function. They also work with more models, even if the model has no Nav function. 

I've used [dynamicWatch](https://dynamicwatch.zendesk.com/hc/en-us/articles/360007071432-How-it-works) in the past on non-Fenix watches to display maps during multi-day hikes. 


## Find GPS file for your route - or make one.
#### Finding GPS route files
Depending on route, it can be fairly easy to find GPS files - usually saved in GPX format.
Bike routes can be searched for in various locations including:
* https://www.gmap-pedometer.com/
* https://ridewithgps.com/find
* For Munros:
	* https://www.walkhighlands.co.uk/perthshire/schiehallion.shtml
	* https://www.haroldstreet.org.uk/waypoints/download/?hillnumber=314

#### Making GPS route files
We can make a route using various tools. 
###### Online Tools (these let you save and export routes):
* https://ridewithgps.com/routes
	* Export as GPX 'track' file for more granular mapping (i.e. more points in route).
	* Export as GPX 'route' file for less granularity.
* https://www.plotaroute.com/myroutes
* https://www.gmap-pedometer.com/
* Or in the online [Garmin Connect](https://connect.garmin.com/modern) app


###### Desktop Tools
See notes [below](Navigating%20with%20Garmin%20Fenix.md#^19d51d) on various Windows tools available but my preferred solution is [JGPSTrackEdit](Navigating%20with%20Garmin%20Fenix.md#^8085bc)

[GPXSee](Navigating%20with%20Garmin%20Fenix.md#^25ee35) is a close second for viewing files but doesn't allow conversion.

I've also heard reasonable things about [Garmin's Basecamp](https://www.garmin.com/en-US/shop/downloads/basecamp) app. You can create a route directly Basecamp, even if you didn’t buy their maps. Before you start, you need to install some free routable maps. [GPSFileDepot](https://www.gpsfiledepot.com/maps/state/all) is a good place to start. Of note are the [Open Street Map topographic routable](https://www.gmaptool.eu/en/content/usa-osm-topo-routable) and the [Open Street Map routable bicycle](https://garmin.openstreetmap.nl/) (it has trails). Each source has it’s own install directions, read them carefully.
Once your maps have been installed, you can access them in [Garmin Basecamp](https://www.garmin.com/en-US/shop/downloads/basecamp).

---

## Convert the route file
Not all route file-types are supported. Typically the GPX file type is supported. The other file types (KML, FIT, ect) can be converted to GPX using the tools above. 

---

## Import to Watch - Navigation-Capable Watches
For watches with the Navigation function, you simply need to get the route file onto the watch. This can be done via:
1. The online [Garmin Connect](https://connect.garmin.com/modern) app
	* Training -> Courses -> Import (top right)
		*Turn off uBlock or other similar extensions*
	* Once Course imported/created, select the 'Send To Device' option.
	* It will sync to the watch when next sync'ing via wifi, or the Garmin Connect phone app.
2. The Windows [Garmin Express](https://www.garmin.com/en-US/software/express/windows/) app.
3. 

---

## Import to Watch - Non-Navigation-Capable Watches
You'll need an app to display the route on non-Nav capable devices. There are multiple map apps for the watches. When I last used this properly it was back in 2014 and I used [dynamicWatch](https://dynamicwatch.zendesk.com/hc/en-us/articles/360007071432-How-it-works) in the past on non-Fenix watches to display maps during multi-day hikes. 

But there appear to be many more similar maps available now. Suggest checking them out if you need to add routes to non-Nav watches.

###### Useful guides
ForeRunner 305: https://beige-alert.livejournal.com/185138.html
Edge 305: https://frank.kinlan.co.uk/garmin-edge-305-route-planing-tutorial/

---

## Tool List
Additional tools which may come in handy.

### Convert GPS file types
* http://www.gpsies.com/convert.do
* [GPSVisualizer](https://www.gpsvisualizer.com/)
* Windows - [GPSBabel](Navigating%20with%20Garmin%20Fenix.md#^10f626)
	GPSBabel converts waypoints, tracks, and routes between popular GPS receivers such as Garmin or Magellan and mapping programs like Google Earth or Basecamp. Literally hundreds of GPS receivers and programs are supported.


### Windows View / Edit GPS files
* [JGPSTrackEdit](https://sourceforge.net/projects/jgpstrackedit/)
	JGPSTrackEdit is a free, portable, open source GPX viewer and editor for Windows. It is a Java based GPX file viewer which requires Java to be installed to work. Apart from GPX, you can view a variety of routes and GIS data files using it. Some of the supported file formats in it include TCX, KML, ASC, etc. ^8085bc
* [GPXSee](https://www.gpxsee.org/index.html)
	 Free open source GPX viewer for Windows. As it’s name suggests, it is a dedicated GPX file viewer that also supports many more file formats to view GPS data such as IGC, FIT, KML, SLF, TCX, etc. It lets you view GIS data, GPS data, Cadence, Speed, Elevation, Distance, and more. ^25ee35
 * [Viking](https://sourceforge.net/projects/viking/)
	Free open source GPX viewer for Windows. It is good GPS data viewer and analyzer software which you can use to view GPX file. Apart from GPX, it also supports KML file formats to view routes and waypoints. You can also edit tracks and routes using this software.
* [GpsPrune](https://activityworkshop.net/software/gpsprune/)
	Free open source GPX viewer software for Windows. It a nice JAVA based software that lets you view GPS data by importing various files including GPX. It allows you to view and analyze GPX file with a lot of useful tools. You can view all tracks, routes, waypoints, etc., from GPX files with respective details. Plus, you can also modify GPX files as it provides a lot of GPS data editing tools.
* [GPX Editor](https://sourceforge.net/projects/gpxeditor/)
	Free open source GPX editor that you can use to view GPX files. It is a portable GPX file viewer that you can use on the go. You can also view NMEA, KML, NGT, and LOG files in it.
* (Win Store) [GPX viewer and recorder]( https://www.microsoft.com/en-gb/p/gpx-viewer-and-recorder/9nblggh4w2z7?activetab=pivot:overviewtab)
 