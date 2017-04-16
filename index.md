---
title: code.mil
---

<section class="row">
<font size="5"> <center> <strong> Free as in freedom </strong> </center> </font><br><br>
</section>
<section class="row">
  <header class="col-sm-6 col-smmd-offset-3">
    Code.mil supports <strong>free and open source software development</strong> at the U.S. Department of Defense (DoD). The objective is to produce <strong>better software</strong> for the DoD, the nation, and the world, through <strong> community software development </strong>.
  </header>
</section>
<section id="faqs" class="row">
  <table><tr>
    <td class="css3-shadow col-sm-4">
      <div class="panel-body">
        <a href="{% if jekyll.environment == 'staging' %}{% else %}{{ site.baseurl}}{% endif %}{% link _faqs/dod.md %}">
          <h2>DoD Developers</h2>
          How do I open source my work?<br>
          How can I contribute?<br>
	  How do I accept community contributions?
        </a>
      </div>
    </td>
    <td class="css3-shadow col-sm-4">
      <div class="panel-body">
        <a href="{% if jekyll.environment == 'staging' %}{% else %}{{ site.baseurl}}{% endif %}{% link _faqs/civ.md %}">
          <h2>Contributors</h2>
          How can I contribute?<br>
          How can I use an open source DoD project?<br>
	  Why should I contribute?
        </a>
      </div>
    </td>
    <td class="css3-shadow col-sm-4">
      <div class="panel-body">
        <a href="{% if jekyll.environment == 'staging' %}{% else %}{{ site.baseurl}}{% endif %}{% link _faqs/other.md %}">
          <h2>Policy</h2>
          What kind of work can be open sourced?<br>
          How does this work with DoD policy?<br>
          Why should source code be released?
        </a>
      </div>
    </td>
  </tr></table>
</section>
<br>
<br>

{:.brandDiv .brand style="width:100%"}
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
<section class="row">
{% for repo in site.data.projects.GitHubIndividualProjects limit:6 %}
    <div class="col-sm-6">
        <div class="col-sm-12 panel panel-default css3-shadow">
            <h2>{{ repo }}</h2>
            <div class="panel-body">
            <br>Lorum Ipsum
            <br>And lots of info.
            <br>And lots of info.
            </div>
        </div>
    </div>
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
</section>

<section class="row">
  <div class="panel css3-shadow">
  <div class="text-left" markdown="1">

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
var _table_ = document.createElement('table'),
    _tr_ = document.createElement('tr'),
    _th_ = document.createElement('th'),
    _td_ = document.createElement('td');

// Builds the HTML Table out of myList json data from Ivy restful service.
 function buildHtmlTable(arr) {
     var table = _table_.cloneNode(false),
         columns = addAllColumnHeaders(arr, table);
     for (var i=0, maxi=arr.length; i < maxi; ++i) {
         var tr = _tr_.cloneNode(false);
         for (var j=0, maxj=columns.length; j < maxj ; ++j) {
             var td = _td_.cloneNode(false);
                 cellValue = arr[i][columns[j]];
             td.appendChild(document.createTextNode(arr[i][columns[j]] || ''));
             tr.appendChild(td);
         }
         table.appendChild(tr);
     }
     return table;
 }

 // Adds a header row to the table and returns the set of columns.
 // Need to do union of keys from all records as some records may not contain
 // all records
 function addAllColumnHeaders(arr, table)
 {
     var columnSet = [],
         tr = _tr_.cloneNode(false);
     for (var i=0, l=arr.length; i < l; i++) {
         for (var key in arr[i]) {
             if (arr[i].hasOwnProperty(key) && columnSet.indexOf(key)===-1) {
                 columnSet.push(key);
                 var th = _th_.cloneNode(false);
                 th.appendChild(document.createTextNode(key));
                 tr.appendChild(th);
             }
         }
     }
     table.appendChild(tr);
     return columnSet;
 }
var xhr = new XMLHttpRequest();
xhr.responseType = 'json';

xhr.open('GET', 'https://api.github.com/search/repositories?q=topic%3Acode-mil%20pushed%3A%3E2017-03-01&sort=stars&order=desc');
xhr.onload = function() {
  var tmpTable = buildHtmlTable(this.response.items)
  // TODO: Commenting out for now.
  // document.body.appendChild(tmpTable);
};
xhr.send();

</script>
