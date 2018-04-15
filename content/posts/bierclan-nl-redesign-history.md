+++
title = "Bierclan.nl Redesign History"
authors = ["ludo"]
description = ""
tags = []
date = "2008-10-31T10:00:00"
+++

![Bierclan.nl sixth version](bcomv6.png)

[Bierclan.nl](http://bierclan.nl) is the oldest website of mine that is still online. It first appeared on the internet in early 2001, if I recall correctly. This first version was my first attempt at creating a dynamic, interactive website. Just two months ago I released the sixth version that actually made it to the world wide web.

## Bierclan?

The *Bier-Clan Oostelijke Mijnstreek* (or: B-COM) was the name of a project my friends and I started in high school. This all started as a joke, but eventually grew to a group of a few hundred people. We started organizing parties in clubs and bars that attracted a lot of people. But, after graduating from high school in 2003, most of us moved to different places across the Netherlands. This affected the B-COM: there was no longer time to get together and organize parties. This changed the B-COM from a lively community in the real-world to an online communication tool to stay in touch with old school friends. Most of us still meet regularly, but the bierclan.nl website is great for staying up-to-date on the whereabouts of old friends.

## Redesigning the website. Over and over again.

![Bierclan.nl Mockups](designing_bierclan-nl.png)

While browsing through my personal archives, I stumbled upon a lot of attempts to re-design the bierclan.nl website. At the end of the day the counter stopped at thirty different designs in various states of completeness, of which only six were actually published to the world wide web. The image above shows screenshots of these designs. For me personally, the most interesting was to see how the way I created these designs evolved. The designs elapse more than seven years, so it's all there: frames, `font`-tags, table-designs, stylesheets, abusing the general-purpose `div`-tag and more semantic approaches.

Under the hood it unveils an evolution from procedural ASP pages to multiple attempts to create a full-fledged application framework in PHP. This last thing never worked out well enough, so the current version still uses a very ‘flat’ procedural PHP codebase. Although it might not be as pretty as it could be, it is still rock-solid. It has undergone several rounds of refactoring during the past years and has survived my many attempts to come up with something better.

![Final Designs Bierclan.nl](final_designs_bierclan-nl.png)

This new, sixth version is my attempt to extend the life of the current codebase with a few years. It also served as a refresher of my PHP knowledge, after having abandoned it years ago in favor of Ruby and Microsoft .NET. It still fascinates me how easy it is to pick up PHP and hack something together, although it misses a lot of the elegance of a language like Ruby or C#.

So, what started as a redesign of [http://bierclan.nl](bierclan.nl) ended up to be a reunion with my own thoughts. These designs were not the only interesting things that I came across in my archives, I also found my very first website (on [Tomb Raider](http://en.wikipedia.org/wiki/Tomb_Raider)) and even some [QBASIC](http://en.wikipedia.org/wiki/QBASIC) applications that I have written in the days of yore...