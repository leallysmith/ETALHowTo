---
title: Digitizing in QGIS
weight: 1
---

This page will contain step by step instructions for digitizing a riverscape in QGIS. Under each section will be the type of shapefile, name for that shapefile, and fields for the shapefile. Keep in mind that these fields are the minimum and project specific demands may require additional fields. If the project is a large digitizing effort it may be beneficial to have one technician generate a series of blank shapefiles to distribute so that other technicians can copy and paste those shapefiles into their projects. This can help ensure consistency across shapefiles and decrease errors with field types.
The first section will detail useful plugins and the basic mechanics of using QGIS to avoid redundancy in later sections where we will go in depth on how to digitize each layer.

For a cheat sheet that only contains field names and types, [see here](https://docs.google.com/document/d/10IKopN1gDufCflItdEPjOzrOjzYp5hHpO2IO35zVeSE/edit?usp=sharing). [This webmap](https://leallysmith.github.io/LCTWebmap/#9/40.3109/-114.7453) has some good examples of mapping. Caveats abound, they are detailed [here](https://leallysmith.github.io/ETALHowTo/Digitizing%20Riverscapes/).

## Using QGIS to Digitize Riverscapes

An important element of high quality digitized data is maintaining a consistent scale. This means that once you begin digitizing a layer at 1:500 for example, the rest of that layer must be digitized at 1:500 scale. You can zoom in and out a little bit if you need better context but avoid digitizing at a variety of scales. This does not mean you have to use the same scale for the entire project, you only have to maintain that scale for the layer you are working on.

Another consideration is to avoid "spaghetti digitizing" this is where the digitizer does not use snapping and tracing and little holes get left behind that from far away, are not visible, but once you zoom in they become clear. In the example below you can see that the polygons have gaps between them in some places and overlap in others when they should touch but not overlap.

<img src="{{ site.baseurl }}/QGISImages/spaghetti.png" alt="spaghetti" style="width:75%;" />

Some useful plugins to install before digitizing are "Clipper" and "Locate points along lines". Toolbars you'll want to have enabled are Digitizing, Advanced Digitizing, Plugins Toolbar (clipper), Locate Lines (locate points along lines), and Snapping. To enable toolbars, find view then toolbars or right click on the toolbars that are already enabled to see more.



### Shapefile Creation and Editing

Click on <img src="{{ site.baseurl }}/QGISImages/shapefilebutton.PNG" alt="button" style="width:5%;" /> to create a shapefile. 

From here name your shapefile and choose its save location then select which type of shapefile you want, polygon, line, or point. Select an appropriate coordinate system for your site this will generally be NAD83/UTM zone ___. Adding fields can be done by naming the field, selecting what type of field it is and then once that is filled out, click the "Add to Fields List" button. If you forget to add fields in this step, you can also do it from the field calculator after you finish creating the shapefile.

<img src="{{ site.baseurl }}/QGISImages/shapefilescreen.PNG" alt="button" style="width:50%;" />

To begin an edit session, select the add feature button. This will look different depending on whether you are working on a polygon, line, or point. <img src="{{ site.baseurl }}/QGISImages/editsession.png" alt="beginediting" style="width:15%;" />

### Field Calculation

If you use area($geometry) and length($geometry) which is what I recommend then these fields will be calculated using the coordinate system's units. You can check what units your CRS uses by looking it up through a search engine or by double clicking the layer to open the layer properties, then going to information, and under the Coordinate Reference Section (CRS) section the units will be shown. Ensure that the units your CRS uses are meters because that's what we generally use for digitizing units, NAD83/UTM Zone ___ uses meters. If your project needs to be in different units, use the appropriate CRS and change the area_sq_m column to be more representative of what you are using. You can also use $area and $length to calculate using units that you can set under Project > Properties > General > Measurements. If you choose this method be careful to make sure that QGIS doesn't change which units its using.

To calculate fields click on the shapefile you want to calculate for and then either in the attribute table or the ribbon click on <img src="{{ site.baseurl }}/QGISImages/abacus.PNG" alt="button" style="width:5%;" />. Here you can create a field if you didn't during the shapefile creation step or "Update existing field". Select the field you'd like to calculate and enter the formula needed. Once that formula is entered, click "OK" and the fields will be calculated.

area($geometry) - will calculate area in CRS units

length($geometry) - will calculate length in CRS units

'string' - you must enclose strings in '  ' to fill tables in field calculator. Typing 'string' will fill the cells and display string

now() - the date and time at that moment

$y - will calculate the latitude

$x - will calculate the longitude

$area - will calculate area in the project's units NOT the CRS units

$length - will calculate length in the project's units NOT the CRS units

### Symbology

There is a standard set of symbology we use in the lab to ensure all our data looks consistent. This symbology can be found at ~\0_ET_AL\NonProject\etal_Symbology. They are named according to the layer they should be used for. To apply this symbology, navigate to the properties of the shapefile you are symbolizing. You can do this by double clicking on the shapefile in your layer pane. Then, regardless of which tab you are on in the bottom left should be a dropdown that says style. From here, click load style then navigate to the directory outlined above. Select the appropriate QGIS Layer setting, then click load style, then click OK. The shapefile should now be symbolized. Older versions and ArcMap versions of symbology can be found in ~\0_ET_AL\Projects\USA\Utah\BLM_Statewide_Monitoring_Kimbell_Ranch_Bear\wrk_Data\Symbology.

### Geopackaging

Once you've finished digitizing the riverscape, calculating the fields, and applying the proper symbology, you'll need to save all these shapefiles as a geopackage. This allows a user to load in all the layers at once and properly symbolized rather than unsymbolized shapefiles one at a time. To package shapefiles, use the "Package Layers" tool from QGIS. You'll select all your layers in inputs and then select where you want it saved and the name. Then run, now you've created a geopackage! 

### Metadata

This [metadata template](https://usu.box.com/s/kg71wsj4gfl4zcd98wm36wl8p5po8baz) is a good baseline to build your metadata off of. While you may not need the geomorphic units and transects sections you can use that template as a base to build your project metadata on. Name will be your name, Date is the date you started digitizing, you'll then state yes or no regarding whether you've been to site or not, then list your lines of evidence in digitizing, this section is about what sorts of imagery and shapefiles you used for more context of the site. Then, for each layer you'll denote what scale you used for digitizing and then your confidence; low, medium, or high. The confidence of accuracy is also a good place to list what reasons you had for your confidence level.

For creating FGDC CSDGM formatted metadata there are tools in both Arc and QGIS that can help and [this website](https://go.mdeditor.org/#/export). This style of metadata will generally only be necessary if the data you create will end up in a government database. This means that unless you're told to create this specifically, just use the template above.

