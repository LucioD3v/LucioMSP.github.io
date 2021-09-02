---
layout: project
title: 'Alibaba Cloud'
image: /assets/img/categories/alibaba_logo.png
screenshot: /assets/img/categories/alibaba_logo.png
caption: Alibaba Cloud
description: >
 Alibaba Cloud, también conocida como AliCloud, ofrece una gama de servicios de infraestructura, plataforma y aplicaciones en numerosas áreas. Dichas ofertas incluyen servicios de almacenamiento, red, base de datos, análisis, seguridad y plataforma de aplicaciones.
---

{% assign posts = site.categories[page.slug] | default:site.tags[page.slug] | default:site.posts %}

{% if page.title.size > 0 %}
  <header>
   <script data-ad-client="ca-pub-3510124386419898" async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
  <hr class="sr-only"/>
{% endif %}


{% assign date_formats  = site.data.strings.date_formats               %}
{% assign list_group_by = date_formats.list_group_by | default:"%Y"    %}
{% assign list_entry    = date_formats.list_entry    | default:"%d %b" %}

{% for post in posts %}
  {% assign currentdate = post.date | date:list_group_by %}
  {% if currentdate != date %}
    {% unless forloop.first %}</ul>{% endunless %}
    <h2 id="{{ list_group_by | slugify }}-{{ currentdate | slugify }}" class="hr">{{ currentdate }}</h2>
    <ul class="related-posts">
    {% assign date = currentdate %}
  {% endif %}
  {% include components/post-list-item.html post=post format=list_entry %}
  {% if forloop.last %}</ul>{% endif %}
{% endfor %}