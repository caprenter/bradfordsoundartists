---
layout: page
title: Events
permalink: /events/
---

{% assign dateToday = 'now' | date: "%Y-%m-%d" %}

# Upcoming events

{% assign events = site.data.skiddle['results'] | sort: "date" | reversed  %}
{% for event in events %}

{% if event.date > dateToday  %}

{% if event.cancelled !=1  %}

<div class="event-item" markdown="1">
#### {{ event.eventname }}
{{ event.date | date: "%A %d %B %Y" }}
{:class="event-date"}
{% if event.largeimageurl %}
<img class="img-responsive" src="{{ event.largeimageurl }}"/>
{% endif %}
{{ event.description }}<br/>
{% if event.startdate %}Doors: {{ event.startdate | date: "%l:%M%P" }} <br/>{% endif %}
{% if event.entryprice %}£{{ event.entryprice }}{% endif %}

{% if event.link %}[Get Tickets for {{ event.eventname }} on Skiddle]({{ event.link }}){% endif %}

</div>
{% endif %} <!-- not cancelled -->
{% endif %} <!-- in the future -->
{% endfor %}


