---
title: How to digitize riverscapes
weight: 1
---

This page will contain step by step instructions for digitizing a riverscape in QGIS. Under each section will be the type of shapefile, name for that shapefile, and fields for the shapefile. Keep in mind that these fields are the minimum and project specific demands may require additional fields. If the project is a large digitizing effort it may be helpful to have one technician generate a series of blank shapefiles to distribute so that other technicians can copy and paste those shapefiles into their projects. This can help ensure consistency across shapefiles and decrease errors with field types.
The first section will detail useful plugins and the basic mechanics of using QGIS to avoid redundancy in later sections.

## Digitizing in QGIS

Some useful plugins to install before digitizing are "Clipper" and "Locate points along lines"

### Shapefile creation

Click on <img src="{{ site.baseurl }}/QGISImages/shapefilebutton.PNG" alt="button" style="width:5%;" /> to create a shapefile. 

From here name your shapefile and choose its save location then select which type of shapefile you want, polygon, line, or point. Select an appropriate coordinate system for your site. Adding fields can be done by naming the field, selecting what type of field it is and then once that is filled out, click the "Add to Fields List" button.

<img src="{{ site.baseurl }}/QGISImages/shapefilescreen.PNG" alt="button" style="width:50%;" />

### Field Calculation

To calculate fields click on the shapefile you want to calculate for and then either in the attribute table or the ribbon click on <img src="{{ site.baseurl }}/QGISImages/abacus.PNG" alt="button" style="width:5%;" />. Here you can create a field if you didn't during the shapefile creation step or "Update existing field". Select the field you'd like to calculate and enter the formula needed. Once that formula is entered, click "OK" and the fields will be calculated.

area($geometry) - will calculate area

length($geometry) - will calculate length

'string' - you must enclose strings in '  ' to fill tables

now() - the date and time at that moment

### Symbology

There is a set of symbology we use in the lab to ensure all our data looks consistent. This symbology can be found at 0_ET_AL\Projects\USA\Utah\BLM_Statewide_Monitoring_Kimbell_Ranch_Bear\wrk_Data\Symbology. To apply this symbology, navigate to the properties of the shapefile you are symbolozing. You can do this by double clicking on the shapefile in your layer pane. Then, regardless of which tab you are on in the bottom left should be a dropdown that says style. From here, click load style then navigate to the directory outlined above. Select the appropriate QGIS Layer setting, then click load style, then click OK. The shapefile should now be symbolized

### Geopackaging

Once you've finished digitizing the riverscape and applying the proper symbology, you'll need to save all these shapefiles as a geopackage. This allows a user to load in all the layers at once and properly symbolized rather than unsymbolized shapefiles one at a time. To package the, use the "Package Layers" tool from QGIS. You'll select all your layers in inputs and then select where you want it saved and the name. Then run, now you've created a geopackage

## Shapefiles

### Valley Bottom
#### How to:

1. Create a polygon shapefile named valley_bottom
2. Fields: 
    area_sq_m - type decimal (double)
3. Use the "Smooth" tool at default values
4. Remove your old valley_bottom layer from the map and export the new "Smooth" temporary layer, overwriting your old shapefile. Keep the name as valley_bottom
5. Field calculate necessary fields

What is this layer? Valley bottom is the stream/river channels and the nearby low-lying contemporary floodplain. The spatial extent of the valley bottom is defined as the area that could plausibly flood during the contemporary flood regime. This layer also sets the boundaries for the rest of the digitizing effort. 

#### Lines of Evidence: 

In elevation rasters you may see a "shelf" where the elevation changes from flatter valley bottom to steeper hill slopes

You may see a change from dense vegetation to sparse vegetation because slope is too steep

A transition to pine stands

#### Images:

### Valley Bottom Centerline
#### How to:

1. Create a line shapefile named vb_centerline

2. Fields: None

3. Use the polygons to lines tool on the valley bottom shapefile

4. Use the locate points along lines tool from the plugin and input the "Lines" temporary file you just created. Offset 0, interval 1, give it an output name, check the "Add Vertices" box, then run.

5. Use this new points temporary layer as the input for the "Voronoi polygons tool"

6. Using the snapping and trace tools in QGIS, digitize the line that runs down the center of the valley bottom.

What is this Layer?

#### Lines of Evidence: 

Voronoi polygons layer

#### Images:

### Riparian
#### How to: 

1. Create a polygon shapefile
2. Fields:
     area_sq_m - type decimal (double)
     type - type string
3. Copy and paste the valley bottom polygon into the Riparian shapefile, for type, fill in "upland"
4. Digitize the riparian areas and for these polygons enter the type as "riparian"
5. From here, select all the areas labeled as riparian and then clip them from the upland polygon by clicking the "Clipper" <img src="{{ site.baseurl }}/QGISImages/clipper.PNG" alt="button" style="width:5%;" /> icon from the clipper toolbar. 
6. Calculate fields

What is this layer? The riparian layer is our best approximation of the floodplain. Previously we had tried to map floodplain but the lines of evidence were weak. Now we map riparian as a way to approximate the current floodplain without making any false claims as to where the floodplain may really be. This layer delineates upland plants vs. riparian plants.

#### Lines of Evidence:

Perennial riparian vegetation

#### Images:

### Active Channel
#### How to:
​	Fields:
What is this Layer? Active channel is the area of the channel that is modified by average stream discharge. This means includes non wetted features such as islands and bars that are located within the channel.

#### Lines of Evidence:

Clear scouring

Channelization

Bars

#### Images:

### Inundation
#### How to:
​	Fields:
What is this Layer?

#### Lines of Evidence:

Structure nearby affecting flows?

#### Images:

### Dam Crests
#### How to:
​	Fields:
What is this Layer?

#### Lines of Evidence:

Significantly ponded water

Is the dam convex with the current?

Does the dam have a mattress?

Be careful to make sure this isn't a woody debris accumulation.

#### Images:

### Thalwegs
#### How to:
​	Fields:
What is this layer?

#### Lines of Evidence:

Look for areas in the channel that appear darker, these are likely deeper water than the surrounding channel

If there are multiple channels, the main thalweg is likely the one that follows the channel with a name in google map base imagery

#### Images:

### Structures
#### How to:
​	Fields:
What is this layer?

#### Lines of Evidence:

#### Images:

### Confluences and Difluences
#### How to:
​	Fields:
What is this layer?

#### Lines of Evidence:

Thalwegs split

Islands

Determine flow direction by looking at channel heads and slope. Higher elevation is generally upstream and channel heads generally point upstream.

#### Images: