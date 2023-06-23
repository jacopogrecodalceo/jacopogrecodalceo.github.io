---
title: dates
---

{% capture now %}{{'now' | date: '%s' | plus: 0 }}{% endcapture %}

<div>
    <h3>{{ site.data.translations.upcoming[page.collection] }}</h3>
    {% for d in site.data.dates %}

        {% for piece in site[page.collection] %}
            {% if d.what == piece.title %}
                    {% capture p_url %}{{ piece.url | prepend: site.url }}{% endcapture %}
            {% endif %}
        {% endfor %}

        {% capture date %}{{d.when | date: '%s' | plus: 0 }}{% endcapture %}
        {% if date >= now %}
                {{ d.when }}, <a href="{{ p_url }}" > <b>{{ d.what }}</b></a>, <a href="{{ d.site }}" target="_blank"> {{ d.name }}</a>, <a href="{{ d.maps }}" target="_blank"> <i>{{ d.where }}</i></a>, {{ d.city }} ({{ d.country }})<br>
        {% endif %}
    {% endfor %}
</div>
---
<div>
    <h3>{{ site.data.translations.past[page.collection] }}</h3>
    {% for d in site.data.dates %}

        {% for piece in site[page.collection] %}
            {% if d.what == piece.title %}
                    {% capture p_url %}{{ piece.url | prepend: site.url }}{% endcapture %}
            {% endif %}
        {% endfor %}

        {% capture date %}{{d.when | date: '%s' | plus: 0 }}{% endcapture %}
        {% if date < now %}
            {{ d.when }}, <a href="{{ p_url }}" > <b>{{ d.what }}</b></a>, <a href="{{ d.site }}" target="_blank"> {{ d.name }}</a>, <a href="{{ d.maps }}" target="_blank"> <i>{{ d.where }}</i></a>, {{ d.city }} ({{ d.country }})<br>
        {% endif %}
    {% endfor %}
</div>