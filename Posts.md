---

title: Posts
permalink: /Posts/
---

{% for post in site.posts %}
  {% capture this_year %}{{ post.date | date: "%Y" }}{% endcapture %}
  {% capture this_month %}{{ post.date | date: "%B" }}{% endcapture %}
  {% capture prev_year %}{{ post.previous.date | date: "%Y" }}{% endcapture %}
  {% capture prev_month %}{{ post.previous.date | date: "%B" }}{% endcapture %}

  {% if forloop.first %}
    <h4>{{ this_month }} {{ this_year }}</h4>
    <ul>
  {% endif %}
  <li class='mbhalf'><a href="{{ post.url }}" class="black">{{ post.title }}</a></li>

  {% unless forloop.last %}
    {% if this_year != prev_year %}
      </ul>
      <h4 class="mt2">{{ prev_month }} {{ prev_year }}</h4>
      <ul>
    {% else %}
      {% if this_month != prev_month %}
        </ul>
        <h4 class="mt2">{{ prev_month }} {{ prev_year }}</h4>
        <ul>
      {% endif %}
    {% endif %}
  {% endunless %}
{% endfor %}
