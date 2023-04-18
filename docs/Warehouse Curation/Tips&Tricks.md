---
title: Tips and Tricks
weight: 1
---

1. Rule based symbology in QGIS will allow you to use "keywords" in the attribute table to symbolize.

   "AGE_MAX" LIKE 'Phanerozoic - Paleozoic - Permian' will apple symbology to anything that 		contains exactly and only that in the attribute table. But what if you have several entries 		and all you care about is whether or not its Paleozoic? Try "AGE_MAX" LIKE '%Paleozoic%'

​		Rule based symbology may also allow you to define symbologies at different zoom scales.



2. If you need to symbolize something that doesn't have any sort of firm upper limit (length of road in the valley bottom for example) then set the upper limit of the bin to 10,000,000. That should cover any use case the lab has and is what we generally use to be the upper max.