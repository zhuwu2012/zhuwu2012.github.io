---
layout: default
title: Talks
nav_order: 3
---

# Talks
{: .no_toc }

<div class="row" id="myItems">
  <div class="col-sm-12 mb-3">
    {% assign sorted_talk = site.data.talk | sort: 'time' | reverse %}
    {% for talk in sorted_talk %}
    {% assign talk = talk_hash[1] %}
    <div class="card border-light">
      <div class="card-body">
        <h3 class="card-title">{{ talk.title }}</h3>
        <h5 class="card-subtitle mb text-muted pb-1"> 
          {{ talk.type }} at <b>{{ talk.meeting }} {{ talk.time }}</b>, {{ talk.place }} 
        </h5>
        <h5 class="card-text">
          [<a href="/assets/others/{{ talk.pdf_link }}">
            Slides
          </a>]
          [<a href="{{ talk.url }}">
            Website
          </a>]
        </h5>
      </div>
    </div>  
    {% endfor %}   
  </div>    
</div>
