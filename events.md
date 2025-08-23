---
layout: default
title: Events
class: narrow-page
---

## upcoming events

<ul>
  {% for event in site.data.events.upcoming %}
    <li>
         <strong>{{ event.date }}</strong> — 
         {% if event.url %}
           <a href="{{ event.url }}" target="_blank" rel="noopener">{{ event.title }}</a>
         {% else %}
           {{ event.title }}
         {% endif %}
         ({{ event.location }})
       </li>
  {% endfor %}
</ul>

## past events

<ul>
  {% for event in site.data.events.past %}
	<li>
	      <strong>{{ event.date }}</strong> — 
	      {% if event.url %}
	        <a href="{{ event.url }}" target="_blank" rel="noopener">{{ event.title }}</a>
	      {% else %}
	        {{ event.title }}
	      {% endif %}
	      ({{ event.location }})
	    </li>
  {% endfor %}
</ul>