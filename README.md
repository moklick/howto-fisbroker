How to use WFS with QGis
==============

How to download geodata from a fis broker wfs (web feature server) via qgis and save it as a shape file.


#### Find dataset

  1. Go to [fis broker](http://fbinter.stadt-berlin.de/fb/index.jsp)
  2. Choose one of the data sets. For example 'Hausumringe'.
  3. Click 'Zum Downloadlink (WFS)'
  4. Look for the 'Rechneradresse' point. Its an url like this one for the houses in Berlin : [wfs houses](http://fbinter.stadt-berlin.de/fb/wfs/geometry/senstadt/re_hausumringe)

#### Load data with QGis

  1. **Download WFS client plugin.** You can install it via QGis by this steps: 'Plugins' -> 'Manage and Install Plugins...' -> search for 'wfs' -> choose 'WFS 2.0 Client' -> 'Install Plugin'
  2. **Download Geodata.** Open the plugin by clicking on 'Web' -> 'WFS 2.0 Client' -> 'WFS 2.0 Client'. Type in an url of a WFS. For example : http://fbinter.stadt-berlin.de/fb/wfs/geometry/senstadt/re_hausumringe. Click on 'Get Capabilities'. After that you can define a bounding box, a feature limit and a SRS (spatial reference system). For the datasets of houses you must choose featureCount = '550000' and SRS = 'EPSG:4258'.
  3. **Save as shapefile**

If you need to convert the shapefile you can do it with the help of ogr2ogr:

```
$ ogr2ogr -t_srs EPSG:4326 -s_srs EPSG:25833 output.shp input.shp
```
