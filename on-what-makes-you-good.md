---
layout: series
title: On What Makes You Good
description: <Fill in>
comments: true
published: true
---

## On What Makes You Good
<br/>
<img src="img/pexels-artem-beliaikin-1051747.jpeg" width="342" height="228">

*In this series, we are exploring how to be good in a new <br/> environment (industry, organization, team, etc.) and how this <br/> relates to perception. Ironically, we learn that all that is required <br/> is already within ...*

{% if site.categories.on-what-makes-you-good %}
   {% assign posts = site.categories.on-what-makes-you-good | sort: "series-part" %}
   {% for post in posts %}
<a href="{{ post.url }}" title="{{ post.title }}">{{ post.title }} {{ post.sub-title }}</a>
   {% endfor %}
{% endif %}

<br/>
<br/>
<br/>

### Notes
[*Photo by Artem Beliaikin from Pexels*][series-photo]

[series-photo]: https://www.pexels.com/photo/come-in-we-re-awesome-sign-1051747/