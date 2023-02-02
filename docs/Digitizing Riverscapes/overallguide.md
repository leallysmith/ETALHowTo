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

<img src="{{ site.baseurl }}/QGISImages/shapefilescreen.PNG" alt="button" style="width:15%;" />

### Field Calculation

To calculate fields click on the shapefile you want to calculate for and then either in the attribute table or the ribbon click on <img src="{{ site.baseurl }}/QGISImages/abacus.PNG" alt="button" style="width:5%;" /> Here you can create a field if you didn't during the shapefile creation step or "Update existing field". Select the field you'd like to calculate and enter the formula needed. Once that formula is entered, click "OK" and the fields will be calculated.

area($geometry) - will calculate area

length($geometry) - will calculate length

'string' - you must enclose strings in '  ' to fill tables

now() - the date and time at that moment

### Symbology

## Shapefiles

### Valley Bottom
How to:
1. Create a polygon shapefile named valley_bottom
1. Fields: 
	area_sq_m - type decimal (double)

What is this layer? Valley bottom is the stream/river channels and the nearby low-lying contemporary floodplain. The spatial extent of the valley bottom is defined as the area that could plausibly flood during the contemporary flood regime. This layer also sets the boundaries for the rest of the digitizing effort. 

Lines of Evidence: 

In elevation rasters you may see a "shelf" where the elevation changes from flatter valley bottom to steeper hill slopes

You may see a change from dense vegetation to thin vegetation because slope is too steep

A transition to pine stands

Images:

### Valley Bottom Centerline
How to:
	Fields:
What is this Layer?

Lines of Evidence:

Images:

### Riparian
How to:
	Fields:
What is this layer?

Lines of Evidence:

Images:

### Active Channel
How to:
	Fields:
What is this Layer?

Lines of Evidence:

Images:

### Inundation
How to:
	Fields:
What is this Layer?

Lines of Evidence:

Images:

### Dam Crests
How to:
	Fields:
What is this Layer?

Lines of Evidence:

Images:

### Thalwegs
How to:
	Fields:
What is this layer?

Lines of Evidence:

Images:

### Structures
How to:
	Fields:
What is this layer?

Lines of Evidence:

Images:

### Confluences and Difluences
How to:
	Fields:
What is this layer?

Lines of Evidence:

Images: