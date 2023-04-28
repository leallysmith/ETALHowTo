---
title: Tips & Tricks
weight: 1
---

###  Tips, Tricks, & Troubleshooting

- For inundation you can either create a new shapefile or duplicate the active channel one and build on that, whichever makes more sense to you
- A lot of the the features you can digitize via reshape <img src="{{ site.baseurl }}/QGISImages/reshape.PNG" alt="reshape" style="width:5%;" />, add vertices <img src="{{ site.baseurl }}/QGISImages/vertex.PNG" alt="vertex" style="width:5%;" />, or adding features and merging <img src="{{ site.baseurl }}/QGISImages/merge.PNG" alt="merge" style="width:5%;" /> them. That way you can save frequently and not lose progress if QGIS crashes. For example, thalwegs can be easier if you start and finish a shape with a couple vertices, and then use the modify vertices tool to add vertices to the end, that way you can save more frequently in the event that QGIS crashes.
- Some projects may require additional fields, like a field for site id, for things like that don't worry about filling out those features every time you get a pop up, you can use the field calculator to fill all the cells at once which is a nice time saver.
- In some cases the trace and reshape tools may not work even if they're enabled. Occasionally in the snapping toolbar it may have unselected what you are snapping to, make sure that there isn't a blank box in the snapping toolbar there and that you're snapping to segments and vertices on all layers. If that doesn't fix it, use the "Fix Geometry" tool on the layer you're trying to trace or the layer you're reshaping, and finally try completely closing QGIS and relaunching it. Additionally, trace may not behave as expected if there are too many vertices in view, in these cases simply zoom in and try again.
- There are a number of digitized projects under ~\0_ET_AL\Projects\USA\Nevada\LCT\Wrk_data\HUC_16040101_Upper_Humboldt\Marys\GIS , you can check that folder to see many desert sites that have been digitized under dry and wet conditions to see how they look.
- For a drone captured ~1.5km site, generally digitizing valley bottom somewhere at 1:1000 or 2000 scale is sufficient, riparian in the ballpark of 1:1000 or 500, and the remaining layers between 1:125 and 1:500. This may not apply to your site but is a good starting point.
- If there is no clear thalweg you can use use the centerline of the channel, then modify that to fit the channel where you can see the thalweg.
- If you plan to have one technician create a series of blank shapefiles they may want to consider going into the layer properties of that shapefile and modifying the attributes form so that every time a feature is added or changed a specific calculation will autopopulate fields. However, evaluate the usefulness of this feature for your project, I won't be covering that method here.
- Sometimes you may need to digitize the active channel but you can't see it. In these cases do your best to approximate where the channel is and digitize a thalweg that follows where you believe the channel is. Once that is done you can create a buffer using what sections of the channel you can see to determine the width of the buffer. You can then edit this buffer to better match the channel where you can see it and then use the buffer for where you can't see it.
- If you want some 3D context, use google earth or the obliques from the drone if available

