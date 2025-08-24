---
layout: default
title: Events
class: narrow-page
---

{% assign now = site.time | date: '%s' %}
{% assign events_sorted = site.data.events | sort: "date" %}

## upcoming events
<ul class="events-list">
  {% assign shown = false %}
  {% for e in events_sorted %}
    {% assign e_epoch = e.date | date: '%s' %}
    {% if e_epoch >= now %}
      {% assign shown = true %}
      <li>
				<span class="event-date">{{ e.date }}</span>
				<span class="event-details">
					<span class="event-chunk event-title">
		        {% if e.url %}
		          <a href="{{ e.url }}" target="_blank" rel="noopener">{{ e.title }}</a>
		        {% else %}
		          {{ e.title }}
		        {% endif %}
					</span>
		
					{% if e.info %} 
						<span class="event-chunk event-info">{{ e.info }}</span> 
					{% endif %}
		
			    {% if e.location %}
						<span class="event-chunk event-location">({{ e.location }})</span>
					{% endif %}
					
					<!--{% if e.media-link %}
						<a href="{{ e.media-link }}" target="_blank" rel="noopener">[{{ e.media-text }}]</a>
			    {% endif %}-->
				</span>
      </li>
    {% endif %}
  {% endfor %}
  {% unless shown %}<li>No upcoming events.</li>{% endunless %}
</ul>

## past events
<ul class="events-list">
  {% assign shown = false %}
  {% for e in events_sorted reversed %}
    {% assign e_epoch = e.date | date: '%s' %}
    {% if e_epoch < now %}
      {% assign shown = true %}
      <li>
		<span class="event-date">{{ e.date }}</span>
		<span class="event-details">
			<span class="event-chunk event-title">
				{% if e.url %}
		      <a href="{{ e.url }}" target="_blank" rel="noopener">{{ e.title }}</a>  
		   	{% else %}
		      {{ e.title }}
		    {% endif %}
			</span>
		
			{% if e.info %} 
				<span class="event-chunk event-info">{{ e.info }} </span>
			{% endif %}
		
	    {% if e.location %} 
				<span class="event-chunk event-location">({{ e.location }})</span>
			{% endif %}
			
			<!--{% if e.media-link %}
				<span class="event-chunk">
					<a class="event-media-link" href="{{ e.media-link }}" target="_blank" rel="noopener">[{{ e.media-text }}]</a>
				</span>
	    {% endif %}-->
		</span>
      </li>
    {% endif %}
  {% endfor %}
  {% unless shown %}<li>No past events yet.</li>{% endunless %}
</ul>

<!--

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
</ul> -->