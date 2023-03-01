---
title: How to digitize riverscapes
weight: 1
---

This page will contain step by step instructions for digitizing a riverscape in QGIS. Under each section will be the type of shapefile, name for that shapefile, and fields for the shapefile. Keep in mind that these fields are the minimum and project specific demands may require additional fields. If the project is a large digitizing effort it may be beneficial to have one technician generate a series of blank shapefiles to distribute so that other technicians can copy and paste those shapefiles into their projects. This can help ensure consistency across shapefiles and decrease errors with field types.
The first section will detail useful plugins and the basic mechanics of using QGIS to avoid redundancy in later sections where we will go in depth on how to digitize each layer.

For a cheat sheet that only contains field names and types and not a complete guide on how to do them, [see here](https://docs.google.com/document/d/10IKopN1gDufCflItdEPjOzrOjzYp5hHpO2IO35zVeSE/edit?usp=sharing).

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

###  Tips, Tricks, & Troubleshooting

- For inundation you can either create a new shapefile or duplicate the active channel one and build on that, whichever makes more sense to you
- A lot of the the features you can digitize via reshape <img src="{{ site.baseurl }}/QGISImages/reshape.PNG" alt="reshape" style="width:5%;" />, add vertices <img src="{{ site.baseurl }}/QGISImages/vertex.PNG" alt="vertex" style="width:5%;" />, or adding features and merging <img src="{{ site.baseurl }}/QGISImages/merge.PNG" alt="merge" style="width:5%;" /> them. That way you can save frequently and not lose progress if QGIS crashes. For example, thalwegs can be easier if you start and finish a shape with a couple vertices, and then use the modify vertices tool to add vertices to the end, that way you can save more frequently in the event that QGIS crashes.
- Some projects may require additional fields, like a field for site id, for things like that don't worry about filling out those features every time you get a pop up, you can use the field calculator to fill all the cells at once which is a nice time saver.
- In some cases the trace and reshape tools may not work even if they're enabled. Occasionally in the snapping toolbar it may have unselected what you are snapping to, make sure that there isn't a blank box in the snapping toolbar there and that you're snapping to segments and vertices on all layers. If that doesn't fix it, use the "Fix Geometry" tool on the layer you're trying to trace or the layer you're reshaping, and finally try completely closing QGIS and relaunching it. Additionally, trace may not behave as expected if there are too many vertices in view, in these cases simply zoom in and try again.
- There are a number of digitized projects under ~\0_ET_AL\Projects\USA\Nevada\LCT\Wrk_data\HUC_16040101_Upper_Humboldt\Marys\GIS , you can check that folder to see many desert sites that have been digitized under dry and wet conditions to see how they look.
- For most sites generally digitizing valley bottom somewhere at 1:1000 or 2000 scale is sufficient, riparian in the ballpark of 1:1000 or 500, and the remaining layers between 1:125 and 1:500. This does not apply to all sites so use your discretion.
- If there is no clear thalweg you can use use the centerline of the channel, then modify that to fit the channel where you can see the thalweg.
- If you plan to have one technician create a series of blank shapefiles they may want to consider going into the layer properties of that shapefile and modifying the attributes form so that every time a feature is added or changed a specific calculation will autopopulate fields. However, evaluate the usefulness of this feature for your project, I won't be covering that method here.
- Sometimes you may need to digitize the active channel but you can't see it. In these cases do your best to approximate where the channel is and digitize a thalweg that follows where you believe the channel is. Once that is done you can create a buffer using what sections of the channel you can see to determine the width of the buffer. You can then edit this buffer to better match the channel where you can see it and then use the buffer for where you can't see it.
- If you want some 3D context, use google earth or the obliques from the drone if available

## Shapefiles

### Valley Bottom
#### How to:

1. Create a polygon shapefile named valley_bottom.shp

2. Fields: 

    area_sq_m - type decimal (double)

    date - type date

    waterbody - type string

3. Digitize the valley bottom

4. Use the "Smooth" tool at default values

5. Remove your old valley_bottom layer from the map and export the new "Smooth" temporary layer, overwriting your old shapefile. Keep the name as valley_bottom

6. Field calculate necessary fields

What is this layer? Valley bottom is the stream/river channels and the nearby low-lying contemporary floodplain. The spatial extent of the valley bottom is defined as the area that could plausibly flood during the contemporary flood regime. **THIS SETS THE EXTENT OF YOUR DIGITIZING. None of the remaining shapefiles from this point on should exceed your valley bottom.**

#### Lines of Evidence: 

In sufficiently resolved elevation rasters such as ones derived from drones you may see a "lip" where the elevation changes from flatter valley bottom to steeper hill slopes rapidly.

You may see a change from dense vegetation to sparse vegetation because slope is too steep to support vegetation.

If there is a VBET run for your area, that is also a good line of evidence

#### Images:

<img src="{{ site.baseurl }}/QGISImages/vbshelf.png" alt="shelf" style="width:75%;" />

### Valley Bottom Centerline
#### How to:

1. Create a line shapefile named vb_centerline.shp

2. Fields: None

3. Use the polygons to lines tool on the valley bottom shapefile

4. Use the locate points along lines tool from the plugin and input the "Lines" temporary file you just created. Offset 0, interval 1, give it an output name, check the "Add Vertices" box, then run.

5. Use this new points temporary layer as the input for the "Voronoi polygons tool"

6. Using the snapping and trace tools in QGIS, digitize the line that runs down the center of the valley bottom.

What is this layer? This line shows the center of the valley bottom. This can be used in conjunction with ac_centerline to determine sinuosity. It's useful for data processing after digitizing

#### Lines of Evidence: 

Voronoi polygons layer

#### Images:

<img src="{{ site.baseurl }}/QGISImages/vbcenter.PNG" alt="vb centerline" style="width:50%;" />

### Riparian
#### How to: 

1. Create a polygon shapefile named riparian.shp

2. Fields:

     area_sq_m - type decimal (double)

     type - type string
     - riparian
     - upland

     date - type date

     waterbody - type string

3. Copy and paste the valley bottom polygon into the Riparian shapefile, for the type, fill in "upland"

4. Digitize the riparian areas and for these polygons enter the type as "riparian", ensure trace is enabled for areas that abut the valley bottom.

5. From here, select all the areas labeled as riparian and then clip them from the upland polygon by clicking the "Clipper" <img src="{{ site.baseurl }}/QGISImages/clipper.PNG" alt="button" style="width:5%;" /> icon from the clipper toolbar. (You can also do riparian in step 3 and then upland in step 4, do what makes more sense)

6. Calculate fields

What is this layer? The riparian layer is our approximation of the floodplain. Previously we had tried to map floodplain but the lines of evidence were weak. Now we map riparian as a way to approximate the current floodplain without making any false claims as to where the floodplain may really be. This layer delineates upland plants vs. riparian plants.

#### Lines of Evidence:

Perennial riparian vegetation

In desert systems riparian can sometimes be the only greenery in the valley bottom

If the riparian stands are dead, this does not count as riparian

Suppression of upland vegetation growth indicates riparian

NDVI raster if available

#### Images:

<img src="{{ site.baseurl }}/QGISImages/riparian.png" alt="riparian" style="width:75%;" />

### Active Channel
#### How to:

1. Create a polygon shapefile named active_channel.shp

2. Fields:

   area_sq_m - type double

   date - type date

   waterbody - type string

3. Digitize the channel edge, this includes bars and islands that are in the channel

4. Calculate fields

What is this layer? Active channel is the area of the channel that is modified by average stream discharge. This means it includes non wetted features such as islands and bars that are located within the bankful channel.

#### Lines of Evidence:

Clear signs of scouring

Channelization

Bars

Elevation raster may show the channel

Breaks in the tree line

Greener areas beside the channel

Generally no non-aquatic vegetation, in non-perennial systems there may be some grasses growing in the channel during the dry season

#### Images:

<img src="{{ site.baseurl }}/QGISImages/ac.PNG" alt="ac" style="width:75%;" />

### Active Channel Centerline

#### How to:

1. Create a line shapefile named ac_centerline.shp

2. Fields: None

3. Use the polygons to lines tool on the active channel shapefile

4. Use the locate points along lines tool from the plugin and input the "Lines" temporary file you just created. Offset 0, interval 1, give it an output name, check the "Add Vertices" box, then run.

5. Use this new points temporary layer as the input for the "Voronoi polygons tool"

6. Using the snapping and trace tools in QGIS, digitize the line that runs down the center of the active channel.

What is this layer? This line shows the center of the active channel. This can be used in conjunction with vb_centerline to determine sinuosity.

#### Lines of Evidence: 

Voronoi polygons layer

#### Images:

<img src="{{ site.baseurl }}/QGISImages/accenter.PNG" alt="ac centerline" style="width:50%;" />

### Dam Crests

#### How to:

1. Create a new line shapefile named dam_crests.shp

2. Fields:

   dam_state - type string

   - intact
   - breached
   - blown_out

   date - type date

   waterbody - type string

3. Trace the crest of each observed dam, in cases where the dam has damage, trace where the crest would be if it was intact

4. Calculate fields


What is this layer? This layer traces the top crest of a dam to show location, extent, and state of the dam. The options for dam_state are intact, where the dam is intact, breached, where the dam has some damage but is still ponding water at a lowered level, and blown_out where there is structural damage the whole height of the dam so it is not ponding water. Ponded water should be traced along the dam crest line if a dam crest is present, then the free flowing after should trace that same dam crest line.

#### Lines of Evidence:

Ponded water

Dams are generally convex with the current

Does the dam have a mattress? A mattress is branches that lay on the downstream side of a dam parallel to the current to help dampen the strength of any overflow and prevent scouring at the base of a dam.

Be careful to make sure this isn't a woody debris accumulation.

"Bath tub" ring of mud around the perimeter of the dam indicating a relatively recent breach

Area of concentrated flow at the location of the breach

#### Images:

<img src="{{ site.baseurl }}/QGISImages/breached.png" alt="breached" style="width:50%;" />

<img src="{{ site.baseurl }}/QGISImages/intactdam.PNG" alt="intact" style="width:50%;" />

### Inundation

#### How to:

1. Duplicate the active_channel layer by exporting it and saving as inundation.shp. If you prefer you can make a polygon from scratch rather than reshaping and building on the active_channel shapefile.

2. Fields:

   type - type string
   - free_flowing
   - ponded
   - overflow

   area_sq_m - type double

   date - type date

   waterbody - type string

3. Using the reshape and add ring tools, modify the polygon to fit where there is water. This is also a good place to use clipper because each of these inundation types is mutually exclusive.

4. Calculate fields

What is this layer? This layer shows where the water is within the valley bottom. Free flowing is water that is flowing in the channel unobstructed, ponded is water that is being ponded by some sort of structure, generally a beaver dam, overflow is water that is being structurally forced onto the floodplain and out of the channel, or a structurally forced secondary channel.

#### Lines of Evidence:

Are there surrounding structures that may be affecting the flow?

Is there water in the system?

Dams can back up water much further than you may expect.

#### Images:

<img src="{{ site.baseurl }}/QGISImages/inundation.PNG" alt="inundation" style="width:75%;" />

### Thalwegs
#### How to:

1. Create a line shapefile named thalwegs.shp

2. Fields:

   type - type string
   - primary
   - secondary

   length - type double

   date - type date

   waterbody - type string

3. Digitize along the deepest part of the channels you've previously digitized, ensure snapping is enabled so that thalweg segments connect to each other

4. Calculate fields

What is this layer? This layer delineates the deepest part of the channel for the whole length of the channel. The primary thalweg is the thalweg that runs through the main channel, secondary thalwegs run along side channels and areas where the primary thalweg may split due to structures in the stream or islands. 

#### Lines of Evidence:

Look for areas in the channel that appear darker, these are likely deeper water than the surrounding channel

In systems that are dry or drying, whatever remaining water is in the channel likely follows the thalweg

The primary thalweg is the thalweg in the larger channel, if there are two channels that are similar sizes, use the channel that follows the google maps trace of the river and has a name.

#### Images:

<img src="{{ site.baseurl }}/QGISImages/thalweg.PNG" alt="thalweg" style="width:75%;" />

<img src="{{ site.baseurl }}/QGISImages/thalweg2.PNG" alt="thalweg" style="width:75%;" />

### Confluences and Difluences

#### How to:

1. Create a point shapefile named confluence_difluence.shp

2. Fields:

   type - string

   - D
   - C
   - C/D

   date - type date

   waterbody - type string

3. Digitize c/ds where there are thalwegs that meet and split

4. Calculate fields

What is this layer? This layer maps flow patterns in a channel. Confluences are where water meets and difluences are where water splits. C/D can be used where one area has both a difluence and a confluence, you can also place a C and a D point at these places if that makes more sense to you rather than one C/D point.

#### Lines of Evidence:

Thalwegs converge or diverge

Islands

Determine flow direction by looking at channel heads and slope. Higher elevation is generally upstream and channel heads generally point upstream.

#### Images:

<img src="{{ site.baseurl }}/QGISImages/cd.PNG" alt="cd" style="width:75%;" />

### Structures

#### How to:

1. Create a shapefile named structures.shp

2. Fields:

   type - type string

   - live 
   - inorganic
   - jam
   - lwd
   - BDA
   - PALS

   date - type date

   waterbody - type string

3. Digitize features by placing points atop structures where you observe them.

3. Calculate fields

What is this layer? This layer can contain low tech restoration structures and other structures that are structurally forcing flows. This means that flows in some way are being modified by these structures, modification of course exists for every size of structure down to a grain of sand if you get pedantic however, for the sake of digitizing flow modification should be visible from aerial imagery. This can include bank erosion, new channels, split flows, pond formation, etc. Which set of structures you digitize may be project specific but generally digitize them all and then apply either the structures symbology or restoration structures symbology. Live means vegetation growing in the channel, inorganic can be things like boulders or tires, a jam is woody debris that is channel spanning and ponding water, lwd is large woody debris in the channel such as a fallen tree, BDAs or beaver dam analogues are human made structures meant to mimic the function and form of a beaver dam, PALS or post assisted log structures are logs being held in the channel by posts, PALS are also made by humans. Dams are should not be digitized in this shapefile because they are already digitized in dam_crests.

#### Lines of Evidence:

Structurally forced flows

Signs of geomorphic modification

PALS may have small circles in the structure visible from aerial imagery, those are the posts

Shapefile indicating location of LTPBR structures

#### Images:

<img src="{{ site.baseurl }}/QGISImages/boulders.PNG" alt="inorganic" style="width:75%;" />
