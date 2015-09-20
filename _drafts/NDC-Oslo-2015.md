---
title: "NDC Oslo 2015"
date: 2015-09-20 20:08
category: [Blog]
tags: [notes, conference, ndcoslo]
published: true
---

We're very lucky [developers at Esendex](http://www.esendex.co.uk/careers) to be able to pick any conference we would like to go to, once a year. We're limited by a shared budget, of course, but this year I was very privileged to go to [NDC Oslo](http://ndcoslo.com/) for a full three days.

I've been to Oslo before, which certainly helped me get around; but the city still amazed me *despite* the conference. However, the conference was the main attraction and it did not disappoint me. I only wish I wasn't suffering from a horrible cold during my time there - I may have enjoyed it even more!

<!--more-->

# Notes

I'm a fan of keeping notes from the talks I see at conferences. They help me refer back to what made the talk good, especially when I present my visit to my colleagues.
For each of the talks, I've prepared a notes page, each with an embedded video of the talk.

Some of the notes are missing, probably because I didn't take notes for that particular talk or I've not typed them up yet. All videos but one are available; click through to see them.

## Wednesday 17th June
<ul>
{% for page in site.pages %}{% if page.event == "NDC Oslo 2015" %}{% assign dayofweek = page.date | date: '%w' %}{% if dayofweek == '3' %}
<li>
  {{ page.date | date: '%H:%M' }} <a href="{{ page.url }}">{{ page.title }}</a> <em>by {{ page.speaker.name }}</em>
</li>
{% endif %}{% endif %}{% endfor %}
</ul>

## Thursday 18th June
<ul>
{% for page in site.pages %}{% if page.event == "NDC Oslo 2015" %}{% assign dayofweek = page.date | date: '%w' %}{% if dayofweek == '4' %}
<li>
  {{ page.date | date: '%H:%M' }} <a href="{{ page.url }}">{{ page.title }}</a> <em>by {{ page.speaker.name }}</em>
</li>
{% endif %}{% endif %}{% endfor %}
</ul>

## Friday 19th June
<ul>
{% for page in site.pages %}{% if page.event == "NDC Oslo 2015" %}{% assign dayofweek = page.date | date: '%w' %}{% if dayofweek == '5' %}
<li>
  {{ page.date | date: '%H:%M' }} <a href="{{ page.url }}">{{ page.title }}</a> <em>by {{ page.speaker.name }}</em>
</li>
{% endif %}{% endif %}{% endfor %}
</ul>