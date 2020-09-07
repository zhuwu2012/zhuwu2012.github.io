---
layout: default
title: Research
nav_order: 2
---

<span id="top"></span>

# Publications
{: .no_toc }

<!-- {% assign sorted_publications = site.data.publications | where:"type",type | sort: 'year' %}
{% for paper in sorted_publications %}
{% assign paper = paper_hash[1] %}
<ul class="list-group list-group-flush">
  <li class="list-group-item">
    <p> {{ paper.title }} </p>
    <a href="{{ paper.citation_url }}">
    </a>
    {% for author in paper.authors %}
    	{{ author.name }},
    {% endfor %}
  </li>
</ul>
{% endfor %} -->


<div class="row" id="myItems">
  {% assign types = "Job market paper, Equity holding network, Innovation network, Machine learning" | split: ", " %}
  {% assign counter = 0 %}
  {% for type in types %}
  <div class="col-sm-12 mb-3">
    <span id="{{ type | join: '_' }}"></span>
    <h2 style="display:inline;"> {{ type }} </h2>
    <h5 style="text-align:right;float:right;"><a href="#top">[ Top ]</a></h5> 
    {% assign sorted_publications_year = site.data.publications | where:"work_type",type | sort: 'id' | group_by: 'year' %}
    {% for paper_year in sorted_publications_year %}
    {% assign papers = paper_year.items | sort: 'order' %}
    {% for paper in papers %}
    {% assign counter = counter | plus: 1 %}
    <div class="card border-light">
      <div class="card-body">
        <h3 class="card-title">{{ counter }}. {{ paper.title }}</h3>
        <h5 class="card-subtitle mb-2 text-muted pb-1"> 
          {% for author in paper.authors %}
            {% if forloop.index < paper.authors.size %} 
              {% if author.name == 'Wu Zhu' %}
                <b>{{ author.name }}</b>,
              {% else %} {{ author.name }},
              {% endif %}
            {% else %} 
              {% if author.name == 'Wu Zhu' %}
                <b>{{ author.name }}</b>
              {% else %} {{ author.name }}
              {% endif %}
            {% endif %}
          {% endfor %}
          ({{ paper.year }})
        </h5>
        <h5 class="card-text"> 
          {{ paper.source }}
        </h5>
        <h5 class="card-subtitle mb-2 pb-1" id="category"> 
          {{ paper.status }}
        </h5>
        <h5 class="card-subtitle mb-2 pb-1" id="category" style="display: none;"> 
          Categories: 
          {% for topic in paper.topic %}
            {% if forloop.index < paper.topic.size %} 
              {{ topic.topic }},
            {% else %} 
              {{ topic.topic }}
            {% endif %}
          {% endfor %}
        </h5>
        <h5 class="card-text"> 
          [<a data-toggle="collapse" data-target="#collapseAbstract{{ paper.id }}" aria-expanded="false" aria-controls="collapseAbstract{{ paper.id }}" href="">
            Abstract
          </a>]
          {% if paper.citation_url %}
            [<a href="{{ paper.citation_url }}">
              SSRN
            </a>]
          {% endif %}
          {% if paper.journal_url %}
            [<a href="{{ paper.journal_url }}">
              Published version
            </a>]
          {% endif %}
        </h5>
        <div class="collapse" id="collapseAbstract{{ paper.id }}">
          <div class="container">
            <p style="text-align:justify">
            {{ paper.abstract }}
            </p>
          </div>
        </div>
        <div class="collapse" id="collapseDescription{{ paper.id }}">
          <div class="container">
            <hr/>
            {{ paper.description }}
          </div>
        </div>
      </div>
    </div>  
    {% endfor %}
    {% endfor %}
  </div>
  {% endfor %}
</div>



<script>
  function myFunction() {
    var input, filter, cards, cardContainer, h5, title, i;
    input = document.getElementById("myFilter");
    filter = input.value.toUpperCase();
    cardContainer = document.getElementById("myItems");
    cards = cardContainer.getElementsByClassName("card");
    for (i = 0; i < cards.length; i++) {
        title = cards[i].querySelector(".card-body h3.card-title");
        authors = cards[i].querySelector(".card-body h5.card-subtitle");
        type = cards[i].querySelector(".card-body h5.card-text");
        category = cards[i].querySelector("[id='category']");
        if (title.innerText.toUpperCase().indexOf(filter) > -1 | authors.innerText.toUpperCase().indexOf(filter) > -1 | type.innerText.toUpperCase().indexOf(filter) > -1 | category.innerText.toUpperCase().indexOf(filter) > -1 ) {
            cards[i].style.display = "";
        } else {
            cards[i].style.display = "none";
        }
    }
  }

  function categorySelector(topic) {
    var cardContainer, cards;
    cardContainer = document.getElementById("myItems");
    cards = cardContainer.getElementsByClassName("card");
    for (i = 0; i < cards.length; i++) {
        category = cards[i].querySelector("[id='category']");
        if ( category.innerText.indexOf(topic) > -1 | topic == "All") {
            cards[i].style.display = "";
        } else {
            cards[i].style.display = "none";
        }
    }
  }

  $(".dropdown-menu a").click(function(){
    $(this).parents(".input-group-append").find('.btn').html($(this).text());
    $(this).parents(".input-group-append").find('.btn').val($(this).data('value'));
  });
</script>
