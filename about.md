---
title: About
layout: default
---

{% include pageHeader.html %}

{% include about/contact.html %}

<section class="row">
  <div class="col-sm-8 col-sm-offset-2 col-xs-12">
    <h4>Code.mil is a product of the <a href="https://dds.mil" title="dds.mil">Defense Digital Service</a> and of collaborators from around the DoD and <a href="http://www.mil-oss.org" title="mil-oss.org">Military Open Source Software</a> community. It's an effort to adapt the norms of free and open software development to the specific needs of the DoD. For the rest of the US Government see the efforts at <a href="https://code.gov" title="code.gov">code.gov</a>.</h4>
  </div>
</section>
<section class="row" id="about">    
  <div class="panel css3-shadow">
    <div class="panel-body">
      <h2>Defense Digital Service Recommendations for Open Source DoD Projects</h2>
      <p>
        The U.S. Department of Defense faces unique challenges in developing open source software and delivering software to the community. This site assists developers of military software in meeting these challenges safely and efficiently, so they can focus on what counts: solving tough problems for our military, the nation, and the world. This site itself is an open source DoD project led by the Defense Digital Service and supported by a community inside and outside of the DoD. If code.mil doesn't do quite  what you need,then you can help make it better!
      </p>
      <p>
        Software licensing is one main challenge. Unlike most software projects, code written by U.S. Federal government employees typically does not have copyright protections under U.S. and some international laws. This can make it hard to understand how to attach an open source license to our code. Defense Digital Service offers licensing approaches and strategies for choosing the best license for your project.
      </p>
      <p>
        Releasing source can also be a major challenge. Procedures for releasing information from many DoD organizations haven't changed much from the days when information took the form of paper reports that traveled by hand from the author, to editors, to the typing pool, and to the supervisory chain of command. Source code is both a written document and a working machine that can create new information and develop furthere in unforeseen ways. This complexity can cause existing information channels to freeze up due to confusion, misunderstandings, and misconceptions. The site provides strategies for this aspect of software release as well. 
      </p>
      <p>
        Defense Digital Service has technical, legal and administrative resources available to assist U.S. Department of Defense agencies in evaluating its software projects for general release. Please see:
      </p>
      <ul>
        <li>
          Our <a href="{% if jekyll.environment == 'staging' %}{% else %}{{ site.baseurl}}{% endif %}/">Defense Digital Service Recommendations for Open Source DoD Projects</a>
        </li>
        <li>
          Contact us at <a href="https://www.dds.mil/" title="dds.mil">dds.mil</a>
        </li>
      </ul>
    </div>
  </div>
  <div class="panel css3-shadow">
    <div class="panel-body">
      <h3>This project's goal</h3>
      <p>
        We are motivated to help the U.S. Department of Defense maintain technical superiority by engaging the brightest public minds in its projects. This best practice is openly embraced in the private sector and we are helping adopt this practice in the public sector.
      </p>
      <p>
        The Defense Digital Service is an agency team of the U.S. Digital Service, which is part of the Executive Office of the President. Recommendations that we provide are NOT official Department of Defense policy. We are collaborating with legal and leadership roles throughout Department of Defense agencies to ensure that our advice is relevant.
      </p>
    </div>
  </div>
  <div class="panel css3-shadow">
    <div class="panel-body">
      <h3>Get involved</h3>
      <p>
        Please see <a href="https://github.com/deptofdefense/code.mil/" title="https://github.com/deptofdefense/code.mil/">our GitHub project page</a> to participate in updating our recommendations.
      </p>
    </div>
  </div>
</section>