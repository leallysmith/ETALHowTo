---
title: Curating Projects for Riverscapes Viewer
weight: 1
---

TODO

Add images for using github tools



Overview of the task: Curation is the process of creating symbology for the three flavors of the Riverscapes Viewer (RV). These are QRV (QGIS), ArcRV (ArcMap), and WebRV (Mapbox/"The Warehouse"). QRV symbology is stored as a .qml, ArcRV is stored as .lyr, and WebRV is stored as a .json for vector data and .txt for raster data.

### Workflow

1. If you don't already have one, create a GitHub account and request to be added to the Riverscapes Organization.

2. Download Github Desktop or GitKraken. Desktop has a less confusing UI, but Kraken is much more powerful and the complex UI is more informative.

3. Clone the RiverscapesXML repository to your local system.

4. Create your own branch so that changes you make won't impact the main branch of the repository. 

5. When you begin to make changes on your branch these will not automatically be reflected in the cloud version aka "the remote" of your branch, only the local version on your computer. To ensure changes you make are reflected in the cloud "commit" your changes frequently. This is essentially "saving" but to the cloud. Then you'll want to "push" those commits which will update the version of your branch that is online.

6. Now you're going to modify the business logic, here is where you specify what symbology name each layer will search for. It is important that the .lyr, .qml and .json (.txt for rasters) that you will soon make all have the same name. Then in the business logic you will use that name for the "symbology =" field. Here is where you can also specify transparency. DO NOT apply transparency to the symbologies, nothing will break if you do it just creates inaccuracies for RV's visualizations.You also shouldn't include the file extension when you specify what symbology each layer should use. For example, the Raster layer below will search for a symbology called "LUIRaster" and apply 40% transparency.

   ``` <Node label="Land Use Intensity Raster" xpath="Raster[@id='LUI']" type="raster" symbology="LUIRaster" transparency="40" /> ```

7. Create the symbology in ArcMap first. We can then convert this into QML using a premium edition of SLYR. If you prefer to start in QGIS that is alright but you'll have to recreate the symbology in ArcMap because the SLYR plugin can't convert into LYR. Only LYR to QML

8. Download and use the SLYR plugin, you'll need to request the license key from someone in the lab. I won't be posting it here because this is a public site. This step will translate the ArcMap symbology into QGIS symbology.

   > Important: Before installing the licensed version of SLYR, you must first uninstall the community version (if installed) and restart QGIS
   >  Download the [installer](https://usuwatershed:JloiY%24%29o%7Bskp@north-road.com/qgis_plugins/2872eb8e-bc44-46ac-9f11-f124c0ce4915/slyr_install.zip)
   >
   > Unzip the downloaded file, and then drag the extracted "install_slyr_qgis.py" over a running QGIS install. The script will add a connection to the private plugins repository, and install the SLYR plugin for you.
   >
   > After the plugin is installed, the SLYR options dialog will open. You must enter your unique license key at this screen, exactly as it appears at the end of this email.
   >
   > To use the plugin, simply drag and drop ESRI lyr, mxd, style, pmf or sxd  files onto the main QGIS window. Alternatively, use the QGIS browser panel to locate lyr,  mxd or style files and right click these for the available conversion  options. The plugin also adds a new "SLYR" group to the Processing toolbox which contains numerous tools for converting and managing ESRI documents.
   >
   > Support for SLYR can be obtained by emailing support@north-road.com.
   >
   > Please send us ANY files you have issues converting and we will investigate ASAP!

9. Converting the symbology is as easy as dragging the LYR file into your project pane and then exporting it to a QML. Check to make sure that all the symbology is correct and transferred correctly, simpler symbologies with only colors, shapes, and labels should transfer error free. More complex symbology that includes expressions may require some edits post transfer.

10. Move to MapBox to create symbology for the web viewer.

11. [![video thumbnail](https://img.youtube.com/vi/0CrZr9Bs9hk/0.jpg)](https://www.youtube.com/watch?v=0CrZr9Bs9hk)

    Cashe has created a video that will explain curation in MapBox which can be a little more complicated but this video will help explain how to do it. Additionally here are links to guides that Matt has written for [raster](https://rave.riverscapes.net/Technical_Reference/Symbology/webrave_rasterramp.html) and [vector](https://rave.riverscapes.net/Technical_Reference/Symbology/webrave_symbology.html) symbology for WebRV.

12. Once you've created these symbologies and placed them in the appropriate folder and modified the business logic for whichever project you're working on, submit a pull request and assign it to Matt or Jordan, once they approve your pull request it will be merged in with the main branch and given to the world!

13. At this point, delete your branch and make a new one to work off of for more symbology. You cannot continue working on the branch you were previously on once it has been merged since it will become outdated and create errors.