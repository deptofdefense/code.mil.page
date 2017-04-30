---
title: Press
layout: default
---

{% include pageHeader.html %}
{% for press in site.news %}
<section class="row" id="post">
  <div class="col-xs-12 panel css3-shadow">    
    <h2><a class="post-link" href="{% if jekyll.environment == 'staging' %}{% else %}{{ site.baseurl}}{% endif %}{{ press.url }}">{{ press.title | escape }}</a></h2>
    <div class="panel-body text-left">
      <div>{{ press.date | date: "%b %-d, %Y" }}</div>
      {{ press.content }}
    </div>
  </div>
</section>
{% endfor %}