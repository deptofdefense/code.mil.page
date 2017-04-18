---
title: code.mil
layout: default
---

<section class="row">
  <div class="col-sm-6 col-sm-offset-3">
    <p class="text-center" style="font-weight:bolder; font-size:2em;">Free as in freedom </p>
    Code.mil supports <strong>free and open source software development</strong> at the U.S. Department of Defense (DoD). The objective is to produce <strong>better software</strong> for the DoD, the nation, and the world, through <strong> community software development </strong>.
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
<br>
<br>

{:.text-center .title}
The DoD OSS Directory

<section class="row">
  <div class="col-sm-3 col-sm-offset-3">
  <button class=" col-sm-12 btn btn-default btn-lg">Submit a Repo</button>
  </div>
  <div class="col-sm-3">
  <button class="col-sm-12 btn btn-default btn-lg">View the Catalog</button>
  </div>
</section>
<br>
<section class="row" id="repos">
<script>
// TODO: Will not scale, need Jenkins or AWS Lambda to update code.json
function addFields(p,response){
  var tmp = document.createElement('h2');
  tmp.innerText = response.full_name;
  p.appendChild(tmp);
  var div = document.createElement('div');
  div.classList.add('panel-body');
  p.appendChild(div);
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

<section class="row">
  <div class="panel css3-shadow" markdown="1">

# Defense Digital Service Recommendations for Open Source DoD Projects

The U.S. Department of Defense faces unique challenges in developing open source software and delivering software to the community. This site assists developers of military software in meeting these challenges safely and efficiently, so they can focus on what counts: solving tough problems for our military, the nation, and the world. This site itself is an open source DoD project led by the Defense Digital Service and supported by a community inside and outside of the DoD. If code.mil doesn't do quite  what you need, then you can help make it better!

Software licensing is one main challenge. Unlike most software projects, code written by U.S. Federal government employees typically does not have copyright protections under U.S. and some international laws. This can make it hard to understand how to attach an open source license to our code. Defense Digital Service offers licensing approaches and strategies for choosing the best license for your project.

Releasing source can also be a major challenge. Procedures for releasing information from many DoD organizations haven't changed much from the days when information took the form of paper reports that traveled by hand from the author, to editors, to the typing pool, and to the supervisory chain of command. Source code is both a written document and a working machine that can create new information and develop furthere in unforeseen ways. This complexity can cause existing information channels to freeze up due to confusion, misunderstandings, and misconceptions. The site provides strategies for this aspect of software release as well. 

Defense Digital Service has technical, legal and administrative resources available to assist U.S. Department of Defense agencies in evaluating its software projects for general release. Please see:

* Our [Defense Digital Service Recommendations for Open Source DoD Projects](implementation-guide.html)
* Contact us at [https://www.dds.mil/](https://www.dds.mil/)

## This project's goal

We are motivated to help the U.S. Department of Defense maintain technical superiority by engaging the brightest public minds in its projects. This best practice is openly embraced in the private sector and we are helping adopt this practice in the public sector.

The Defense Digital Service is an agency team of the U.S. Digital Service, which is part of the Executive Office of the President. Recommendations that we provide are NOT official Department of Defense policy. We are collaborating with legal and leadership roles throughout Department of Defense agencies to ensure that our advice is relevant.

## Get involved

Please see [our GitHub project page](https://github.com/deptofdefense/code.mil/) to participate in updating our recommendations.

<p class="rss-subscribe">subscribe <a href="{{ "/feed.xml" | relative_url }}">via RSS</a></p>

  </div>
  </div>
</section>

<script>
// TODO: Example of a search
var xhr = new XMLHttpRequest();
xhr.responseType = 'json';

xhr.open('GET', 'https://api.github.com/search/repositories?q=topic%3Acode-mil%20pushed%3A%3E2017-03-01&sort=stars&order=desc');
xhr.onload = function() {
  // TODO: Commenting out for now.
  // document.body.appendChild(tmpTable);
};
// xhr.send();

</script>
