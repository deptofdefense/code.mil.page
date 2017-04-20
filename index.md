---
title: code.mil
layout: default
---

<section class="row">
  <div class="col-sm-2 col-sm-offset-2">
    <img class="img-responsive" src="{% if jekyll.environment == 'staging' %}{% else %}{{ site.baseurl }}{% endif %}{% link _assets/birdplaceholder.png %}" alt="DDS.mil" />
  </div>
  <div class="col-sm-6">
    <h4>Code.mil supports <strong>free and open source software development</strong> at the U.S. Department of Defense (DoD). The objective is to produce <strong>better software</strong> for the DoD, the nation, and the world, through <strong> community software development </strong>.</h4>
  </div>
</section>
<section id="faqs" class="row">
  <table><tr>
    <td class="css3-shadow col-sm-4">
      <a href="{% if jekyll.environment == 'staging' %}{% else %}{{ site.baseurl}}{% endif %}{% link _faqs/dod.md %}">
        <div class="panel-body">
          <h2>DoD Developers</h2>
          How do I open source my work?<br>
          How can I contribute?<br>
	  How do I accept community contributions?
        </div>
      </a>
    </td>
    <td class="css3-shadow col-sm-4">
      <a href="{% if jekyll.environment == 'staging' %}{% else %}{{ site.baseurl}}{% endif %}{% link _faqs/civ.md %}">
        <div class="panel-body">
          <h2>Contributors</h2>
          How can I contribute?<br>
          How can I use an open source DoD project?<br>
	  Why should I contribute?
        </div>
      </a>
    </td>
    <td class="css3-shadow col-sm-4">
      <a href="{% if jekyll.environment == 'staging' %}{% else %}{{ site.baseurl}}{% endif %}{% link _faqs/other.md %}">
        <div class="panel-body">
          <h2>Policy</h2>
          What kind of work can be open sourced?<br>
          How does this work with DoD policy?<br>
          Why should source code be released?
        </div>
      </a>
    </td>
  </tr></table>
</section>

<section class="row" id="repos">
  <div class="text-center title">The DoD OSS Directory</div>

  <div class="col-sm-3 col-sm-offset-3">
  <button class=" col-sm-12 btn btn-default btn-lg">Submit a Repo</button>
  </div>
  <div class="col-sm-3">
  <button class="col-sm-12 btn btn-default btn-lg">View the Catalog</button>
  </div>
</section>
<section class="row" id="repos">
<script>
// TODO: Will not scale, need Jenkins or AWS Lambda to update code.json
function addFields(p,response){
  var div = document.createElement('div');
  div.classList.add('panel-body');
  p.appendChild(div);
  var [a,b] = response.full_name.split("/");
  var tmp = document.createElement('div');
  tmp.innerText = a;
  div.appendChild(tmp);
  tmp = document.createElement('h2');
  tmp.innerText = b;
  div.appendChild(tmp);
  var array = [response.description
            ,"Last Updated: " + response.pushed_at.slice(0,9)
            ,response.language];
  for (var i=0;i<array.length;i++){
    tmp = document.createElement('p');
    tmp.innerText=array[i];
    div.appendChild(tmp);
  }
}
</script>
<script>
// Cache repo info in localStorage
function updateRepo(repo){
  var cache = localStorage.getItem(repo + ".date");
  var p = document.currentScript.parentNode;
  // 15 min invalidation
  if (Date.now() - Number.parseInt(cache) < 900 * 1000) {
    return addFields(p,JSON.parse(localStorage.getItem(repo)));
  }
  var xhr = new XMLHttpRequest();
  xhr.responseType = 'json';
  xhr.open('GET', 'https://api.github.com/repos/' + repo);
  xhr.onload = function() {
    if (xhr.readyState !== 4 ) { return }
    var response;
    if (xhr.status == 403) {
      console.log('Rate limit reached. Using localStorage');
      response = JSON.parse(localStorage.getItem(repo));
      if (!response) response = {full_name:repo,description : '',pushed_at:'',language:''};
    }
    else if (xhr.status !== 200 && xhr.status !== 304) {
      console.log(xhr.status);
      response = {full_name:repo,description : '',pushed_at:'',language:''};
    }
    else {response = xhr.response;}
    addFields(p,response);
    // Cache response
    localStorage.setItem(repo,JSON.stringify(response));
    localStorage.setItem(repo + ".date",Date.now());
  };
  xhr.send();
};

value = {{ site.data.projects.GitHubIndividualProjects | jsonify }};
</script>
{% for repo in site.data.projects.GitHubIndividualProjects limit:6 %}
    <div class="col-sm-6">
        <a href="https://github.com/{{repo}}" class="col-sm-12 panel panel-default css3-shadow">
            <script>updateRepo("{{repo}}");</script>
        </a>
    </div>
{% endfor %}
</section>

<section class="row">
<div class="col-sm-6">
<h2>Recent blog posts</h2>
{% for post in site.posts %}
  <div class="panel css3-shadow col-sm-12">
    {% assign date_format = site.minima.date_format | default: "%b %-d, %Y" %}
    <span class="post-meta">{{ post.date | date: date_format }}</span>
    <h2>
     <a class="post-link" href="{% if jekyll.environment == 'staging' %}{% else %}{{ site.baseurl}}{% endif %}{{ post.url }}">{{ post.title | escape }}</a>
    </h2>
  </div>
{% endfor %}
</div>
<div class="col-sm-6">
<h2>In the News</h2>
{% for post in site.news %}
  <div class="panel css3-shadow col-sm-12">
    {% assign date_format = site.minima.date_format | default: "%b %-d, %Y" %}
    <span>{{ post.date | date: date_format }}</span>
    <h2>
     <a href="{% if jekyll.environment == 'staging' %}{% else %}{{ site.baseurl }}{% endif %}{{ post.url }}">{{ post.title | escape }}</a>
    </h2>
  </div>
  {% endfor %}
</div>
</section>


<script>
// TODO: Example of a search
/*
var xhr = new XMLHttpRequest();
xhr.responseType = 'json';

xhr.open('GET', 'https://api.github.com/search/repositories?q=topic%3Acode-mil%20pushed%3A%3E2017-03-01&sort=stars&order=desc');
xhr.onload = function() {
  // TODO: Commenting out for now.
  // document.body.appendChild(xhr.response);
};
 xhr.send();
*/

</script>
