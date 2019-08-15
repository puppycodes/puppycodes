---
layout: page
title: archives
navigation: true
---

<span>instagram: <a style="text-decoration:underline !important" href="https://puppycodesarchive.nyc3.cdn.digitaloceanspaces.com/archive.zip">archive.zip</a></span>



<br>



<section class="post wrapper">
{% for post in site.posts %}
  {% assign currentdate = post.date | date: "%Y" %}
  {% assign yeardate = site.time | date: "%Y" %}
  {% if currentdate != date %}
  {% if currentdate != yeardate %}
  <!--/posts-archive-->
  {% endif %}
<p class="post-year">{{ currentdate }}</p>
  {% endif %}
  <div class="title">
    <a href="{{ post.url | relative_url }}">

  <span class="page-title">  {{ post.title }} </span>
    </a>
</div>
  {% assign date = currentdate %}
  {% if forloop.last %}

  {% endif %}
{% endfor %}
<!--/posts-->
</section>
