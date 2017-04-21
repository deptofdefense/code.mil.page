---
title: Blog
layout: default
---

<style>
.post-date-box {

}
.post-d {
  font-size: 2em;
}
.post-m {
  font-size:1em;
  height:1em;
}
.post-y {
  font-size:1em;
  
}
</style>
{% include pageHeader.html %}
{% for post in site.posts %}
<section class="row">
  <div class="col-sm-12 panel css3-shadow">    
    <h2><a class="post-link" href="{% if jekyll.environment == 'staging' %}{% else %}{{ site.baseurl}}{% endif %}{{ post.url }}">{{ post.title | escape }}</a></h2>
    <div class="col-sm-1 pull left post-date-box">
      <div class="post-d">{{ post.date | date: "%d" }}</div>
      <div class="post-m">{{ post.date | date: "%b" }}</div>
      <div class="post-y">{{ post.date | date: "%Y" }}</div>
    </div>
    <div class="col-sm-11">
      <div class="panel-body text-left">
        {{ post.content }}
      </div>
    </div>
  </div>
</section>
{% endfor %}