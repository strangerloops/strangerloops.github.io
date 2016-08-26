---
layout: post
title:  "the walk of shame, or: visualizing pedestrian permeability"
date:   2016-08-04 22:13:44 -0400
categories: nyc
---

new york state's [open data portal][nysdata] contains the address of every business with an on-premises liquor license (i.e. somewhere you can buy and drink alcohol, i.e. a bar). [mapzen's valhalla][valhalla] is a free and open source routing engine. put them together and you can get walking directions from every bar in new york to your address. here's every bar to my apartment:

![image-title-here](/assets/bklyn.png){:class="img-responsive"}

[make your own here][wos]

**but wait there's more!**

i'm in the midst of reading *the death and life of great american cities*, jane jacobs's 1961 polemic against the orthodox urban planning theory of the time and an instant classic. the book's principal tenet is that streets and neighborhoods are kept safe, vibrant, and economically diverse by pedestrian traffic throughout the day. two key factors[^1] affecting this pedestrian traffic are:

**mixing of primary uses:** if all the nightlife in a neighborhood is on a single street, you'll have pedestrian traffic on that street at night but your residential streets will be deserted/dangerous. whereas, if attractions are evenly spread throughout the neighborhood, they'll draw pedestrians through more streets and keep more of it alive. (this doesn't apply to just nightlife; central business districts consisting almost exclusively of office buildings are active during the day and become dead at night.)

**length of blocks:** in cities where streets are laid out as a grid, the length of blocks determines the number of paths available when heading in an intercardinal direction (northeast, northwest, southeast, southwest). longer blocks pool pedestrians into single corridors and offer them no reason to use streets parallel to their own. moreover, the volume of the pedestrians these corridors collect forces their commerce into standardized, mass-appeal monotony. short blocks offer various alternate paths and open the neighborhood up to pedestrians. don't know why i typed this because these images from the book[^2] explain this 100x better than i just did

![image-title-here](/assets/longblock.png){:class="img-responsive"}
![image-title-here](/assets/shortblock.png){:class="img-responsive"}

later in the chapter, jacobs explains why the upper east side is more vibrant than the west side:

![image-title-here](/assets/jacobs.png){:class="img-responsive"}

**less words more maps**

ok. here's walking home from every bar when you live at 88th & central park west:

![image-title-here](/assets/west.png){:class="img-responsive"}

and here's walking home from every bar when you live at 88th & 5th avenue, directly across from the park:

![image-title-here](/assets/east.png){:class="img-responsive"}

look how much more permeable the east side is! it benefits from additional avenues bisecting its streets as well as more bars in the immediate area.

one more bonus one that nicely illustrates the difference in permeability - walking home from every bar when you live on central park south:

![image-title-here](/assets/south.png){:class="img-responsive"}

i spent too much time on this

[here's the code i used to draw these maps][github] 
inspired by [this thing][er] and by [jane jacobs][jane]

[^1]: there are actually two more, for four total! read the book if the suspense is killing you.
[^2]: these images and the paragraph are from the book 'the death and life of great american cities' which i did not write and am probably not allowed to be reproducing here. don't sue me please

[nysdata]: https://data.ny.gov/
[valhalla]: https://mapzen.com/products/turn-by-turn/
[wos]: https://walk-of-shame.herokuapp.com/
[er]: http://stevecoast.com/2016/01/04/new-kickstarter-every-road/
[jane]: https://en.wikipedia.org/wiki/Jane_Jacobs
[github]: https://github.com/strangerloops/walk-of-shame