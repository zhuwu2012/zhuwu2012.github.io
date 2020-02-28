---
layout: default
title: Teaching
nav_order: 4
---

## Teaching
{: .no_toc }

{% assign courses = site.data.teaching | where:"type","instructor" %}
{% for course in courses %}
{% assign course = course_hash[1] %}
<div class="card border-light">
<div class="card-body"> 
  <h3 class="card-title">{{ course.title }}</h3>
  <h5 class="card-subtitle text-muted pb-2"> 
  {% for time in course.time %}
    {% if forloop.index < course.time.size %} 
    {{ time.time }},
    {% else %} {{ time.time }}
    {% endif %}
  {% endfor %}
  </h5>
  <h5 class="card-text"> 
  </h5>
</div>
</div>

{% endfor %}

<br> 

## TA
{: .no_toc }

{% assign courses = site.data.teaching | where:"type","TA" %}
{% for course in courses %}
{% assign course = course_hash[1] %}
<div class="card border-light">
<div class="card-body"> 
  <h3 class="card-title">{{ course.title }}</h3>
  <h5 class="card-subtitle text-muted pb-2"> 
  {% for time in course.time %}
    {% if forloop.index < course.time.size %} 
    {{ time.time }},
    {% else %} {{ time.time }}
    {% endif %}
  {% endfor %}
  </h5>
  {% if course.more %}
  <h5 class="card-text"> 
  	<a href="{{ course.more }}">Data Science Live (DSL)</a>
  </h5>
  {% endif %}
</div>
</div>
{% endfor %}