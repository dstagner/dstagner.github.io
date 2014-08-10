---
layout: page
title: Hello Lunch!
tagline: Confessions of a Living Room CEO
---
{% include JB/setup %}

{% for post in site.posts %}
<div class="panel panel-default">
  <div class="panel-heading">
    <h3 class="panel-title"><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a>
      <small class="pull-right">{{ post.date | date_to_string }}</small>
    </h3>
  </div>
  <div class="panel-body">
    {{ post.content }}
  </div>
</div>
{% endfor %}

