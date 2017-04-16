---
title: code.mil
---

<style>
#faqs > table td[class*="col-"], table th[class*="col-"] {
  position: relative;
}
section a {
  color: black;
}
.panel:hover {
    background: #eee;
}
section > .btn {
    margin-bottom: initial;
}

</style>
<section class="row">
<header class="col-sm-6 col-sm-offset-3">
Code.mil is an <strong>experiment in open source</strong> at the U.S. Department of Defense (DoD). The goal is to <strong>foster open collaboration with the developer community</strong> across the world on DoD open source projects.
</header>
</section>
<section id="faqs" class="row">
<table><tr>
<td class="css3-shadow col-sm-4">
<a href="{% if jekyll.environment == 'staging' %}{% else %}{{ site.baseurl}}{% endif %}{% link _faqs/dod.md %}">
<h2>Active duty and DoD civilians</h2>
How do I open source my work?<br>
How can I contribute?
</a>
</td>
<td class="css3-shadow col-sm-4">
<a href="{% if jekyll.environment == 'staging' %}{% else %}{{ site.baseurl}}{% endif %}{% link _faqs/civ.md %}">
<h2>Citizen contributors</h2>
How can I contribute?<br>
What do I need to know when using an open source DoD project?
</a>
</td>
<td class="css3-shadow col-sm-4">
<a href="{% if jekyll.environment == 'staging' %}{% else %}{{ site.baseurl}}{% endif %}{% link _faqs/other.md %}">
<h2>Policy, Legal, and Press</h2>
What kind of work can be open sourced?<br>
How does this work with DoD policy?<br>
What are the details of how this works?
</a>
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
{% endfor %}
</section>
<br>
<br>
<br>
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

<section markdown="1">

# Defense Digital Service Recommendations for Open Source DoD Projects

The U.S. Department of Defense faces unique challenges in open sourcing its code. Unlike most software projects, code written by U.S. Federal government employees typically does not have copyright protections under U.S. and some international laws. This can make it hard to attach an open source license to our code. Defense Digital Service offers solutions to these problems.

Defense Digital Service has technical, legal and administrative resources available to assist U.S. Department of Defense agencies in evaluating its software projects for general release. Please see:

* Our [Defense Digital Service Recommendations for Open Source DoD Projects](implementation-guide.html)
* Contact us at [https://www.dds.mil/](https://www.dds.mil/)

## This project's goal

We are motivated to help the U.S. Department of Defense maintain technical superiority by engaging the brightest public minds in its projects. This best practice is openly embraced in the private sector and we are helping adopt this practice in the public sector.

The Defense Digital Service is an agency team of the U.S. Digital Service, which is part of the Executive Office of the President. Recommendations that we provide are NOT official Department of Defense policy. We are collaborating with legal and leadership roles throughout Department of Defense agencies to ensure that our advice is relevant.

## Get involved

Please see [our GitHub project page](https://github.com/deptofdefense/code.mil/) to participate in updating our recommendations.

## More agency-specific resources for open source and software release policies

* Department of the Army
  * Research, Development and Engineering Command
    * Army Research Laboratory
      * [The U.S. Army Research Laboratory (ARL) Software Release Process for Unrestricted Public Release](https://github.com/USArmyResearchLab/ARL-Open-Source-Guidance-and-Instructions)
      * [Army Research Laboratory's GitHub organization page](https://github.com/USArmyResearchLab)
        is the preferred publication location for ARL's projects per
        [ARL policy](https://github.com/USArmyResearchLab/ARL-Open-Source-Guidance-and-Instructions).
* General Services Administration
  * 18F
    * [18F Open Source Policy](https://github.com/18F/open-source-policy)

And following is Federal-government-wide policy on source code distribution:

* [U.S. Federal Source Code Policy](https://code.gov/#/policy-guide/docs/overview/introduction])
* [Enterprise code inventory](https://code.gov/#/policy-guide/docs/compliance/inventory-code)

<p class="rss-subscribe">subscribe <a href="{{ "/feed.xml" | relative_url }}">via RSS</a></p>

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
