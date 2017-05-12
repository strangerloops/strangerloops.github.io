---
layout: post
title:  "better biking through open data: (re)introducing PBR"
date:   2017-05-02 23:31:33 -0400
categories: nyc, biking
---

about two years ago, some friends at [Chi Hack Night][chn] and i were throwing around ideas for a bike-related project to work on, and something that emerged early on and stuck was the notion of a context-aware routing algorithm based on open data that also knew its user's preferences. i found, for example, that when traveling north from my apartment i preferred to use a parallel side street to the main street that google maps suggested despite it being a slight detour because it had less traffic and a bike lane. i also found myself being surprised by construction or road work blocking routes i was used to and having to reroute spontaneously.

the idea lay dormant for a while, but when i had three weeks off between gigs last summer, i spent a bunch of time working on it. an iOS app called PBR quietly launched last summer ([and even got some press in Chicagoist!][chicagoist]) but when i became employed again i ran out of time to develop crucial features and solve show-stopping bugs. it's no longer on the app store and gathered dust for a year.

but recently my involvement with [transportation alternatives][ta], [bigapps 2017][bigapps], and the looming [L train shutdown][carto] got me interested in this again, and a (very early) new version of the app can now be found [here][pbr].

**so what is this thing?**

PBR is a navigation app that understands that the best bike route is not the most direct one. it uses data from [OpenStreetMap][osm], which is a free and publicly editable map of the world, to construct weighted directed graphs of cities using a modified instance of the [Open Source Routing Machine][osrm]. this is how it behaves:

- preference for residential streets, which typically have less traffic than main streets.
- preference for one-way streets. these allow cyclists to ride on the left-hand side of the street to reduce the chance of being doored. they also make it easier to pass slow or stalled vehicles from the left because there is no conflicting traffic from the other side of the street. finally, turns onto other one-ways are safer because there's conflicting traffic in only one direction.
- modest preference for class II (unprotected dedicated) bike lanes, which offer dedicated space to ride in. however, many bike lanes are on main streets that are otherwise dangerous, and so the preference for bike lanes is weaker than that for residential streets and oneways. the preference for class I (protected) bike lanes is very strong. class III (sharrows and signed bike routes) do not confer any boost.
- penalty for main streets, which usually have multiple lanes of traffic, making turning and passing dangerous. Main streets are also usually lined with storefronts, causing drivers picking up and dropping off passengers to block bike lanes.
- penalty for truck routes. truck drivers make dangerously wide turns and have large blind spots.

using OSM has advantages too: reliance on open data allows people to easily keep the data used to cost routes correct and up to date. for example, when bushwick got new bike lanes installed last year, i updated OSM that same day. google maps remained out of date for months.

there are actually two OSRM instances running, with slightly different preferences - the black route cares a little more about directness and distance than the blue one, which cares a little more about using streets that are residential or have dedicated bike infrastructure.

selected results that are maybe interesting:

**bushwick to manhattan**

![image-title-here](/assets/pbr/to_manhattan_google.png){:class="img-responsive"}

![image-title-here](/assets/pbr/to_manhattan_pbr.png){:class="img-responsive"}

google has the user turn 10 times to get onto Graham Avenue (two-way, no bike lane) and then turn onto Grand Street. while it has bike lanes, Grand is notoriously unsafe on account of heavy truck traffic and bike lanes being blocked. [Matthew von Ohlen][mvo] was killed by a driver on this street last summer. PBR continues on Evergreen to Moore Street (one-way, residential), uses the parallel Manhattan Avenue (one-way, bike lane) instead of Graham, and avoids Grand Street using Meserole/South 4th.

**manhattan to north brooklyn**

![image-title-here](/assets/pbr/manhattan_google.png){:class="img-responsive"}

![image-title-here](/assets/pbr/manhattan_pbr.png){:class="img-responsive"}

google uses Grand Street (see above for why that's bad). PBR avoids Grand Street (as well as Flushing Avenue, a two-way, four-lane truck route) using Meserole, Seigel, and Bogart (all one-way residential streets.)

**crown heights to greenwood**

![image-title-here](/assets/pbr/greenwood_google.png){:class="img-responsive"}

![image-title-here](/assets/pbr/greenwood_pbr.png){:class="img-responsive"}

google leaves the protected bike lane on Prospect Park West early to access the bike lane on 9th Street. PBR uses 15th Street instead, which, while not having a bike lane, is a quiet one-way residential street, and allows the route to avoid six blocks on 5th Avenue, a two-way with no bike lanes that’s frequently congested on account of being lined with storefronts.

i very much hope to add plenty of features, like profiles for chicago (this project's birthlplace), native iOS and android clients that can save addresses as favorites, bikeshare integration, and searching by place names rather than just addresses in the future. in the meantime, if you've read this far, i'd love to hear your thoughts and/or feedback on routes!

[web client source code][source1] / [OSRM fork source code][source2]

[chn]: https://chihacknight.org/
[chicagoist]: http://chicagoist.com/2016/07/07/new_bike-route_app_allows_riders_to.php
[ta]: https://transalt.org
[bigapps]: http://www.bigapps.nyc/
[carto]: https://carto.com/blog/looking-at-the-l
[pbr]: http://pbr-web.herokuapp.com/
[osm]: https://www.openstreetmap.org/
[osrm]: http://project-osrm.org/
[mvo]: https://patch.com/new-york/williamsburg/matthew-von-ohlen-nyc-bike-lover-bartender-killed-brutal-brooklyn-hit-run
[source1]: https://github.com/strangerloops/pbr-web
[source2]: https://github.com/strangerloops/osrm-backend
