---
title: Curating Projects for Riverscapes Warehouse
weight: 1
---

TODO

Add images for using github tools

Workflow

1. Download Github Desktop or GitKraken. Desktop has a less confusing UI, but Kraken is much more powerful and the complex UI tells you a lot.

2. Copy the RiverscapesXML repository to your local system.

3. Create your own branch so that changes you make won't impact the main branch of the repository.

4. Create the symbology in ArcMap first. We can then convert this into QML using a premium edition of SLYR. If you prefer to start in QGIS that is alright but you'll have to recreate the symbology in ArcMap because the SLYR plugin can't convert into LYR. Only LYR to QML

5. Download and use the SLYR plugin, you'll need to request the license key from someone in the lab. I won't be posting it here because this is a public site. This step will translate the ArcMap symbology into QGIS symbology.

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

6. Check to make sure that all the symbology is correct and transferred correctly

7. Move to MapBox to create symbology for the web viewer.

8. ```
   [![vide0 thumbnail](https://img.youtube.com/vi/0CrZr9Bs9hk/0.jpg)](https://www.youtube.com/watch?v=0CrZr9Bs9hk)
   ```

   Cashe Rasmussen has created a video that will explain curation in MapBox which can be a little more complicated but this video will help explain how to do it.