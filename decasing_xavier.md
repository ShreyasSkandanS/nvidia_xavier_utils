# Decasing the AGX Xavier Developer Kit

### WARNING: NVIDIA does not recommend doing this and neither do I. But we are a research lab afterall focused on lightweight autonomy and that case doesn't cut it for us. 

## 1. Band saw to the top

First we took the carrier board off, removed the screws we believed were holding the board in place and decided to take off the top of the developer board heat sink to take a look inside the fan enclosure. Thanks Jeremy Wang!

![bandsaw](/figs/band_saw.JPG)
![bandsaw_gif](/figs/band_saw_xavier.gif)
![bandsaw_results](/figs/case_top_fins.JPG)

## 2. Detaching the module from the heat sink and thermal enclosure

After taking a look under the hood of the cooling enclosure, it appeared that the only way to pop the module out was to heat it. We put it on a hot plate and pulled the module out. Thanks Yash Mulgaonkar!

![hotplate](/figs/hot_plate_out.JPG)
![exposed1](/figs/exposed_1.JPG)
![exposed2](/figs/exposed_2.JPG)

## 3. Module weight and carrier weight

And for the glory numbers:
![module_weight](/figs/module_weight.JPG)
![carrier_weight](/figs/module_weight_carrier.JPG)

Nvidia has definitely invested a lot of time and engineering skills into building this developer kit. The entire case was designed to help keeping the Xavier cool. I would definitely not recommend doing this as the risk of destroying your module are quite high. This module did boot up afterwards and look to be working fine but let's just say I was lucky.

