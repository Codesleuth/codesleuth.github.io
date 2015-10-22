---
title: "TypeScript, JavaScript, and Beyond"
date: 2015-09-04 11:22
category: [Blog]
tags: [hacking, events]
published: true
pinned: true
---

![Hack Manchester Logo](/img/hack-manchester-logo.png){:class="pure-img"}

Hack Manchester is an annual hack event which takes place in the heart of Manchester at the Museum of Science and Industry. 
Hundreds of people descend on Manchester to spend 25 hours coding up the best solution they can come up with to the challenges set by the sponsors, in the hope to win a flurry of prizes up for grabs.

## Challenges

This year's challenges come from some regular sponsors, and a few from newcomers:

* [WA:UK Tech Angels](http://www.waukta.com/hack-manchester-2015/)
* [Clockwork SMS](https://www.clockworksms.com/blog/clockwork-is-sponsoring-hack-manchester-2015/)
* [AutoTrader](http://careers.autotrader.co.uk/hack-manchester-2015/)
* [RentalCars.com](http://www.rentalcars.com/hackmanchester)
* [The LAD Bible](https://medium.com/the-lad-bible/don-t-talk-about-innovation-make-it-happen-bc47d0a45933)
* [Autodesk](http://adndevblog.typepad.com/aec/2015/09/join-us-at-hackmanchester-in-october.html)
* [Rise](http://thinkrise.com/pages/manchester-challenge.html)

The challenges this year have taken a _turn for the vague_ and haven't impressed me very much. There's some interesting technical challenges to overcome, but the scope for ideas has taken us through the ropes and shrunk to a in-deterministic ramble of rubbish which we're all disappointed with.

### Challenge: WA:UK Tech Angels

This challenge is for the **Best In Show** award.

This can be anything, and doesn't have to be entered in any other challenge either.

> [...] you don't have to enter another challenge to win Best in Show, but it doesn't exclude you if you do. If you don't enter another challenge, you can only win Best in Show. All teams are eligible and automatically considered for Best in Show, and can (and often do) win one of the other challenges as well.  In contrast to the advice I normally give of 'focus on one challenge', entering at least one challenge is not a bad idea. I wouldn't enter more than two though as challenge judges tend to pick ideas that specifically target their challenge.  I've never seen teams that target many challenges win any.
> 
> What does win best in show? Innovation (seriously we see a lot of the same ideas each year - flappy birds clones ain't going to win it) and Execution (if it doesn't work, it doesn't win)

The downside to aiming for Best In Show is that you have _every other hack_ to compete against. It'll be the hardest challenge to win due to the sheer volume of entries.

### Challenge: Clockwork SMS

This is a simple challenge: **The Most Ridiculous Use of ClockworkSMS**

However, "ridiculous" is open to interpretation. Last year the brief read "The Most Pointless Use of Clockwork", which came with some examples we were confused by since they seemed to have a point in some way or another. "Ridiculous" broadens the scope somewhat, and I think this is a challenge you can truly go wild on.

### Challenge: AutoTrader

The brief: **Best use of the open police data-set for Greater Manchester**

> The challenge is to make the most interesting use of the data and APIs available at https://data.police.uk/ that’s relevant to Greater Manchester. Bear in mind we’re looking for something more than just plotting the information via a mapping API

The first thing that comes to mind for any challenge with Police data involved is **safety**. This data can tell you how likely particular crimes will take place by geographic area - useful if you're buying a house or looking for a school to send your kids to. So what new and interesting things can you do with this data? The answer lies with cross-referencing it with other data sources, such as perhaps the [Transport for Greater Manchester data feeds](http://developer.tfgm.com/) or [Tax information from the DataGM project](http://datagm.org.uk/dataset) - information can be extrapolated from this data in more ways than you can imagine; but that's the hard part.

### Challenge: RentalCars.com

Idea: **Use web, mobile or a browser based game technology to make any part of renting cars more personalised and fun**

I'm lost with this one. Is renting cars fun at all? The challenge suggests that it is fun and they would like ideas to improve on that, but I'm honestly struggling with this.
The best ideas we've come up with so far are gamifying the process of renting a car; perhaps a Need For Speed style _car builder_ interface, or a racing system you can play with your mates - they're all terrible ideas. I wish this challenge had nothing to do with renting cars - was that really necessary?

### Challenge: The LAD Bible

Challenge: **Make use of geo-location and social APIs to bring people together and share in the local community (+ volunteering?)**

> The LADbible prides itself on it’s community, so we want teams to come up with an innovative way that lets people volunteer and help out their local community — think Uber for volunteering.
> We’re looking for teams to make use of geo-location and social APIs (Facebook, Twitter, Instagram) to really bring people together and share what they are doing in the community. Lets make it viral!

Straight away I'm thinking "But isn't that just Facebook?"

The angle I'm focussing on is the _volunteering_ part; communities need volunteers for all sorts of reasons ranging through the elderly, disabled, disadvanted and homeless. There are charities for everything, and each one of those can be made better simply by boosting their exposure. But what about solving a problem we've not yet decided we have? Do the elderly like to go out in winter? No. Do they trust people at the door? Rightly not. So how about providing a trusted service that gets things done for them, without them having to go outside?

Perhaps the community angle could be a simple connector between Facebook and Twitter, limited to the local area? Sounds pointless, but if it gets tickboxes filled then perhaps it's not bad.

### Challenge: AutoDesk

Challenge: **Use the AutoDesk View and Data APIs to visualise and interact with 3D data.

> Most innovative, exciting, whacky, crazy, mind blowing use of our View and Data API to visualise and interact with 3D data. We will provide a bunch of datasets on the day (e.g. cars, buildings, city blocks, toasters, etc.) but it would be great to see something completely new.

The [tool](http://lmv.rocks/) they would like you to use is designed for modelling things such as buildings, landscapes, cars, tools and engines. So, the challenge is to like... use the API? You've really got to combine this with another challenge, or be very imaginative, to be able to come up with anything at all interesting.

### Challenge: Rise

Brief: **Use [Estimote Beacons](http://estimote.com/) to help the [Rise commnity](http://thinkrise.com/pages/manchester.html)**

> We want people to come in to collaborate, hack, code, and play. We’ve placed some beacons here just like those at the Rise site on Deansgate, Manchester. How can these beacons be used in conjunction with the information screens, coffee shop, and open meeting rooms available at Rise & the global Rise community? We want to further develop and potentially deploy the best idea at the Rise site!

The beacons sound fun - I can think of numerous things to do with them. However, how many of these ideas are unique to just beacons? Doesn't GPS solve a lot of the problems we already have? The key to winning this challenge will be to abstract beacons into something else, so they can be used as _point of sale_ or _check-in_ tools. They're merely a signal or call to action for users, unless you approach them as a solution to a problem which can be solved with passive scanning (auditing?)

I expect the majority of attendees to try hit this challenge. Depending on the complexity of the API for these things, it may be a worthy challenge to shoe-horn into any idea.

## Summary