---
layout: post
title:  "identifying affordable housing at risk in new york city"
date:   2016-08-04 22:13:44 -0400
categories: nyc
---
[enough][nation] [ink][comptroller] has doubtless [been][indypendent] [spilled][slate] on the topic of new york city's affordable housing crisis, so i'll cut to the chase.

nyc department of finance releases a [spreadsheet][finance] monthly containing records for every property sale in the past year, including the sale's address and price. last year, [john krauss and others][jk] demonstrated that the number of rent stabilized units in every building in the city can be obtained by scraping that building's property tax records. joining these datasets lets us estimate how 'overleveraged' any particular sale of a building containing stabilized apartments is by comparing it to the neighborhood mean per unit. an overleveraged sale is a red flag: buildings containing only rent stabilized apartments should not be selling for 200% of the neighborhood mean per unit, so it's a safe bet that the new owners plan to [force out tenants by whatever means they can][croman].

every dot on this map is a property sale of 6 units or more[^1] occurring between july 2015 and june 2016. the dot's saturation corresponds to how fully rent stabilized that building is (a building with 10/10 stabilized units is opaque; one with 0/10 is transparent)[^2] and its color to how the sale price compares to the neighborhood average (redder is more expensive.) click on any dot for details. take this with as many grains of salt as you would any project built with open government data by a random online man

<iframe width="100%" height="520" frameborder="0" src="https://strangerloops.carto.com/viz/e1e01ec2-5aab-11e6-83a3-0ee66e2c9693/embed_map" allowfullscreen webkitallowfullscreen mozallowfullscreen oallowfullscreen msallowfullscreen></iframe>

the usual suspects are all present - you'll find clusters of opaque, bright red dots in harlem, washington heights, the lower east side, mott haven, and astoria. (anyone know what's going on in fordham hill / university heights in the bronx?) there are also large pockets of moderately overleveraged sales all over brooklyn (check bushwick, greenpoint, flatbush, and crown heights).

some follow up ideas: getting information about the people/companies making these purchases and the mortgages they take out; monitoring 311 reports coming out of these buildings; using historical property sales data to see if sales correlate with future losses in stabilization; preemptive tenant organizing in highly stabilized, overleveraged buildings, etc

[here's the code i used to get all the data][github]

[^1]: just about every building with rent stabilized apartments has six or more units.
[^2]: RS counts for each property were obtained by scraping quarterly property tax bills for june 3, 2016. it would probably have been better to find the latest property tax bill dated before the building's sale but i didn't think of that until now. maybe i'll do that later.

[comptroller]: https://comptroller.nyc.gov/wp-content/uploads/documents/Growing_Gap.pdf
[indypendent]: https://indypendent.org/2016/06/28/amid-growing-housing-crisis-rgb-approves-second-straight-rent-freeze
[nation]: https://www.thenation.com/article/how-to-dump-tenants-and-make-a-fortune-2/
[slate]: http://www.slate.com/articles/business/moneybox/2015/01/nyc_affordable_housing_plan_de_blasio_s_efforts_are_ambitious_and_laudable.html
[finance]: https://www1.nyc.gov/site/finance/taxes/property-rolling-sales-data.page
[jk]: http://blog.johnkrauss.com/where-is-decontrol/
[croman]: http://www.amny.com/real-estate/nyc-landlord-steven-croman-accused-of-forcing-out-rent-stabilized-tenants-to-convert-apartments-1.11779168
[github]: https://github.com/strangerloops/identifying-affordable-housing-at-risk