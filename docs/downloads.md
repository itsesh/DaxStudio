---
title: Downloads
layout: page
---

> This page lists previous releases of DAX Studio - the current release is available from the top of the [homepage](/)

{% assign idx = 0 %}

{% for release in  site.github.releases %} 
  {% if release.draft != true and release.prerelease != true and idx > 0 %}
### {{ release.name }}
    {% for asset in release.assets %}
      {% assign download_count = asset.download_count  %}
      {% assign download_size = asset.size %}
      {% assign download_type = "installer" %}
      {% if asset.content_type == "application/x-zip-compressed" %}
        {% assign download_type = "portable" %}
      {% endif %}
- [{{ release.name }} ({{ download_type}})]({{ asset.browser_download_url }}) <br/>
  Size: {% include filesize.html number=download_size %} \| Date: {% if asset.created_at  %}{{ asset.created_at | date_to_string }} {% else %} N/A {% endif %} \| Downloads: {% include intcomma.html number=download_count %}
     {% endfor %}      


{% comment %}

{% assign asset = release.assets[0] %}
{% assign download_type = "installer" %}
- [{{ release.name }} ({{ download_type}})]({{ asset.browser_download_url }})
  Size: {% include filesize.html number=download_size %} \| Date: {% if asset.created_at  %}{{ asset.created_at | date_to_string }} {% else %} N/A {% endif %}
{% endcomment %}

  {% endif %}
  {% assign idx = 1 %}

{% endfor %}
