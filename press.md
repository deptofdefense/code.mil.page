---
title: Press
---

{% for press in site.news %}
<section class="row">
  <div class="col-sm-12 panel css3-shadow">    
    <h2><a class="post-link" href="{% if jekyll.environment == 'staging' %}{% else %}{{ site.baseurl}}{% endif %}{{ post.url }}">{{ press.title | escape }}</a></h2>
    <div class="panel-body text-left">
      <div>{{ post.date | date: date_format }}</div>
      {{ press.content }}
    </div>
  </div>
</section>
{% endfor %}