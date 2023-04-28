---
title: Tips and Tricks
weight: 1
---

- Rule based symbology in QGIS will allow you to use "keywords" in the attribute table to symbolize.

"AGE_MAX" LIKE 'Phanerozoic - Paleozoic - Permian' will apply symbology to anything that 		contains exactly and only that in the attribute table. But what if you have several entries 		and all you care about is whether or not its Paleozoic? Try "AGE_MAX" LIKE '%Paleozoic%'

AGE_MAX is the column you are telling QGIS to search in LIKE says you're looking for things like your search criteria, and your search criteria is '%Paleozoic%'. The inclusion of the percent symbols tells QGIS that it doesn't matter what comes before or after, as long as the string contains Paleozoic then it is correct. This means whether your field contained Phanerozoic - Paleozoic - Permian, Paleozoic, or peanutPaleozoicbutter all would return as matching the criteria.

​		Rule based symbology may also allow you to define symbologies at different zoom scales.

- If you need to symbolize something that doesn't have any sort of firm upper limit (length of road in the valley bottom for example) then set the upper limit of the bin to 10,000,000. That should cover any use case the lab has and is what we generally use to be the upper max.

- Arcade expressions can be used in ArcMap to help have more control over your symbology. You will need to find helpful resources to explain arcade to you but that is a thing that exists.

- You can import new fonts to MapBox by navigating to where you'd apply fonts in the symbology and then rather than selecting a font from their list you'll click "Manage fonts in your account" and follow the prompts.

