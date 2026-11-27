---
title: Google Earth Engine
subject: 
subtitle: Introduction to geospatial analysis in the cloud using Google Earth Engine
short_title: 3. GEE
exports:
    - format: typst
      template: lapreprint-typst
      output: export/03_gee.pdf
---


Introduction to geospatial analysis in the cloud using Google Earth Engine

## TL;DR

- Google Earth Engine is a rich resource with petabytes of datasets and the ability to analyze data in the cloud rapidly.
- GEE's strength is cloud-based analysis, not visualization. For better visualization/cartographic tools, see Chapters 4, 6, and 8.
- See Chapter 4 and [Geemap](https://geemap.org/) for a way to deploy Earth Engine using Python.

## Scenario

You need to do a quick exploratory data analysis of above- and below-ground carbon biomass for an area of interest near Lake Tahoe in the Central Sierra, California. A donor has asked you to do this by the end of the week. You go down the hall to the room where the map plotters are located and ask the 'GIS guy' for help. He peers up above his array of screens and says he's busy with a dozen other projects; he might be able to get you something in two weeks. He suggests you check out Google Earth Engine.

Yes! You've heard of this and think Google Earth will be easy. But when you check out Earth Engine and find a console with an empty map, the required JavaScript coding is another universe, let alone language. Damn!

## DIY

This scenario applies even if you don't have a GIS guy down the hall with the defunct plotter! So, how do you DIY the donor's needs? 

Google Earth Engine may be one of the most ubiquitous free and open-source software packages for remote sensing and geospatial analysis. Technically, it isn't free or open-source, but individuals, nonprofits, and students can use it for free. Its extensive library and cloud computing capabilities make it an exceptional resource you can use anywhere you have an internet connection on any computer. And it's not that difficult to start, despite using JavaScript!

The full code for this example can be found [here](https://code.earthengine.google.com/609ec9275c6c686b4ddd394f520a27a2).

Once you log into [Earth Engine](https://code.earthengine.google.com/), search for 'carbon' in the search bar at the top of the page. Select Global Aboveground and Belowground Carbon Density Maps. In the lower left of the page, select See example ({numref}`globalabg`).

```{figure} /figures/gee/globalabg.png
:height: 500px
:name: globalabg
Global above and belowground biomass carbon dataset.
```

That will open a new code editor with the following JavaScript code:

```javascript
var dataset = ee.ImageCollection("NASA/ORNL/biomass_carbon_density/v1");

var visualization = {
  bands: ["agb"],
  min: -50.0,
  max: 80.0,
  palette: ["d9f0a3", "addd8e", "78c679", "41ab5d", "238443", "005a32"],
};

Map.setCenter(-60.0, 7.0, 4);

Map.addLayer(dataset, visualization, "Aboveground biomass carbon");
```

Clicking Run in the upper right of the interface will give you a basic map of aboveground biomass ({numref}`abg`).

```{figure} /figures/gee/abg.png
:height: 500px
:name: abg
Aboveground biomass output.
```

You can zoom in or out and click the layer on or off. Selecting the Inspector in the upper right panel will allow you to click on any pixel in the map and get the information from the raster displayed ({numref}`inspector`).

```{figure} /figures/gee/inspector.png
:height: 500px
:name: inspector
Using the inspector tab in the console to get pixel information.
```

In this case, the Mosaic image has four bands related to aboveground and belowground carbon; the latitude and longitude of the clicked point are (-68.16, 1.83), and the pixel size is 10 km. Add the belowground (bgb) carbon with

```javascript
var vis_b = {
  bands: ["bgb"],
  min: -50.0,
  max: 80.0,
  palette: ["D6BCB1", "AB8574", "784E3D", "3D2216", "26140C", "000000"],
};
Map.addLayer(dataset, vis_b, "Belowground biomass carbon");
```

You can zoom the map out and center it to approximately world level by changing line 10 of the code:

```javascript
Map.setCenter(-24.83, 19.88, 2);
```

Hit run or control + enter (windows) or command + enter (mac) to run the new code. Cleaning up the code and adding comments with // to explain what each section does is standard coding practice. The double forward slash allows you to add a comment that does not run when the code executes and is equivalent to the hashtag for Python. You can comment out any line of code by clicking on the line and typing the control/command + enter on your keyboard. A reorganization will give you the following code and image ({numref}`bgb_world`).

```javascript
// Add global carbon density map
var dataset = ee.ImageCollection("NASA/ORNL/biomass_carbon_density/v1");

// Add visual parameter variables
var vis_a = {
  bands: ["agb"],
  min: -50.0,
  max: 80.0,
  palette: ["d9f0a3", "addd8e", "78c679", "41ab5d", "238443", "005a32"],
};

var vis_b = {
  bands: ["bgb"],
  min: -50.0,
  max: 80.0,
  palette: ["D6BCB1", "AB8574", "784E3D", "3D2216", "26140C", "000000"],
};

// Center map and add layers
Map.setCenter(-24.83, 19.88, 2);
Map.addLayer(dataset, vis_a, "Aboveground biomass carbon");
Map.addLayer(dataset, vis_b, "Belowground biomass carbon");
```

```{figure} /figures/gee/bgb_world.png
:height: 500px
:name: bgb_world
Add a world-level carbon density map.
```

Note that the belowground layer now shows up on top. Turn it off by clicking the checkmark in the Layers tab, or, to view it first, reverse the order of the code (e.g., move line 22 to 21). You can alter the layer visibility by changing the `Map.addLayer` command with a true (visible) or false argument (added to map, but not visible) after the layer name:

```javascript
Map.addLayer(dataset, vis_b, "Belowground biomass carbon", false);
```

Note the command structure: Map.addLayer(Dataset or feature to add to the map, visualization parameters, layer name, shown (true or false for shown/not shown), opacity). To see the arguments for any command, click Docs in the left panel and type the command name to search for it. Select the name and the API reference will appear.

## AOI Clip

Getting back to the original request, you can clip the dataset to an area of interest, in this case, around Lake Tahoe. You can clip the map to datasets such as Tiger Lines for states or by country. Clipping by specific shapefiles requires you to upload the vector as a shapefile into Earth Engine. This is fiddly and not as easy as dragging/dropping into Arc, QGIS, or online software such as Felt or Earth Blox. We'll keep this to a simple box.

Turn off the map layers and zoom into your area of interest AOI, in this case near Lake Tahoe ({numref}`tahoe`).

```{figure} /figures/gee/tahoe.png
:height: 400px
:name: tahoe
Zooming to an area of interest. Note the highlighted rectangle/polygon buttons to add geometry vector layers.
```

Enter a search in the box at the top of Earth Engine, such as 'South Lake Tahoe, CA, USA'. In the map pane, click the highlighted 'Draw a Rectangle' button and drag a square over the area ({numref}`aoi`).

```{figure} /figures/gee/aoi.png
:height: 400px
:name: aoi
Rectangle drawn to the area of interest. The default name will be geometry; here it is already renamed bbox.
```

This will add a layer in the imports section at the top of your code called geometry (var geometry: Polygon, 4 vertices). I have changed the name by double-clicking the layer name in the code editor to rename it 'bbox' (double-click geometry, type in bbox, and hit enter), but you can use the name geometry. If you use the default name or name it something else, remember to change the name in the code below from bbox to geometry (or your name). Under the dataset variable, change the code to the ImageCollection as follows:

```javascript
// Add global carbon density map
var dataset = ee
  .ImageCollection("NASA/ORNL/biomass_carbon_density/v1")
  .map(function (image) {
    return image.clip(bbox);
  });
```

Note that the end of the dataset line no longer has a semicolon since the end of the code line now follows the bbox clip. Change the map center and zoom into your bounding box by changing the Map.setCenter function (line 21):

```javascript
// Center map and add layers
Map.setCenter(-120.2348, 38.8744, 9);
```

Alternatively, change the line to Map.centerObject(bbox, 9) for a more memorable way to center. In the map pane, hover over Geometry Imports and uncheck bbox. Run the code again ({numref}`clipped_bg`).

```{figure} /figures/gee/clipped_bg.png
:height: 500px
:name: clipped_bg
Belowground biomass clipped to the area of interest.
```

Given the clash of colors for the brown and green carbon, it might help to change the basemap. Go to [Snazzy Maps](https://snazzymaps.com), select a basemap you like. If you inspect the JavaScript code, you'll notice it adds ~130 lines to your script in the Earth Engine Console. There's an easier way using the [snazzy](https://github.com/aazuspan/snazzy) GitHub repository to reduce the total lines to two. Here, I used the Snazzy grayscale URL:

```javascript
// Change basemap to snazzy subtle grayscale
var snazzy = require("users/aazuspan/snazzy:styles");
snazzy.addStyle("https://snazzymaps.com/style/15/subtle-grayscale", "Gray");
```

Once you hit Enter, you will see 'Gray' as an additional map option in the middle-right portion of your screen, alongside the default 'Map' and 'Satellite' options. Earth Engine offers other customizations you can add with little code, as shown [here](https://developers.google.com/earth-engine/tutorials/community/customizing-base-map-styles), although the Snazzymap customization is much easier to implement.[^base] After adding the gray basemap, the basemap selection bar changes ({numref}`gray`).

[^base]: SnazzyMap customization can slow map loading and doesn't allow basemap customization. To customize a snazzy basemap, go to the basemap you like and click the green pencil on the page; a 'Customize' popup appears when you hover over it. Select the items you want to change, then go back to the JavaScript and paste into your script. You can also remove or correct mislabeled features in the Gulf of Mexico and Lake Ontario! This brings us back to square one: hundreds of lines of extra code just for a basemap. However, if you create a basemap in another file, then in your working script call the basemap using require and a link to the file name (typically 'users/your_user_name/folder:file_name') that will speed up basemap rendering.

```{figure} /figures/gee/gray.png
:height: 100px
:width: 300px
:name: gray
Gray basemap bar after adding the grayscale map.
```

Altogether, the map now looks like {numref}`abg_tahoe` once the belowground layer is turned off.

```{figure} /figures/gee/abg_tahoe.png
:height: 500px
:name: abg_tahoe
Gray basemap bar after adding the grayscale map.
```

The full code is [here](https://code.earthengine.google.com/609ec9275c6c686b4ddd394f520a27a2). Congratulations, you've made your first Earth Engine map. Selecting the Inspector pane in the top right lets you click anywhere on the map to get coordinates and carbon values at the pixel level.

## Geospatial EDA

This type of exploratory data analysis (EDA) is extraordinarily useful for looking at large datasets of multiple biotic and abiotic data types that the Earth Engine Catalog offers. You can search for any dataset in the catalog, click a sample, and instantly review the data. In practice, this is almost like 'no code'. It also computes and adds any layer in the cloud, so it doesn't matter how old or slow your computer is; you can run the geospatial computations in the cloud. This is a tremendous advantage, especially for more complex analyses.

For the map we just made, you'll likely want to add functionality such as a legend showing carbon levels for each raster dataset and a graph with the range of carbon levels for the bounding box area.

## Resources

There are many resources from getting started to the advanced use of Google Earth Engine:

- **Spatial Thoughts, Ujaval Gandhi**. [End-to-End Google Earth Engine](https://courses.spatialthoughts.com/end-to-end-gee.html) provides full course materials that start with setting up the Earth Engine environment and move into more advanced topics such as machine learning and change detection.
- **Remote Sensing with GEE**. If you want to get serious about Google Earth Engine, I highly recommend you read the free online Cloud-Based Remote Sensing with Google Earth Engine [book](https://www.eefabook.org/) by Rebecca Moore et al. This book is worth reading as a standalone remote sensing textbook and expertly guides you through everything from basic to complex geospatial analysis.
- **Awesome-GEE**. The Opengeos [Awesome-GEE](https://github.com/opengeos/Awesome-GEE) GitHub repo is a fantastic curated list of GEE resources. This incredible resource has everything from getting started to courses, papers, datasets, and more. You could lose yourself for days in here!
— **GEE Google Group**. The Google Earth Engine Developers [listserv](https://groups.google.com/g/google-earth-engine-developers) is useful for answering many other questions, especially when you get stuck.
— **Awesome-GEE-Community-Catalog**. Not to be confused with Awesome-GEE, the [Awesome GEE Community Catalog](https://gee-community-catalog.org) is an equally awesome treasure trove of datasets ready for analysis and with sample code to start their use immediately.
- **Visualization and Analysis of Brazil Floods 2024**. This [tutorial] has an excellent workflow design and superb explanations of remote sensing theory and concepts in this [tutorial](https://share.gishub.org/brazil_floods/#create-sentinel-1-sar-composites). In addition, the tutorial contains very useful text and code for analyzing synthetic aperture radar (SAR) imagery.