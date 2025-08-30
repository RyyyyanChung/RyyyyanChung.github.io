---
layout: page
title: Publications
icon: fas fa-newspaper
order: 2
me: "Shao-Hung Chung"
---

<style>
.pub-list {display:grid; grid-template-columns: repeat(auto-fit, minmax(320px,1fr)); gap: 1rem;}
.pub-card {padding:1rem; border:1px solid #e5e7eb; border-radius:12px; background:#fff; box-shadow:0 1px 2px rgba(0,0,0,.06);}
.pub-title {margin:0 0 .25rem; font-weight:600; line-height:1.35;}
.pub-authors,.pub-venue{margin:.15rem 0; font-size:.95rem; opacity:.9;}
.badges a{display:inline-block; font-size:.8rem; text-decoration:none; border:1px solid #d1d5db; padding:.15rem .5rem; border-radius:999px; margin:.25rem .35rem .1rem 0;}
details{margin-top:.4rem}
</style>

{% assign me = page.me | default: site.author.name | default: 'Me' %}
{% assign me_bold = '<strong>' | append: me | append: '</strong>' %}

# Publications

<div class="pub-list">
{% assign pubs = site.data.Publications | sort: 'year' | reverse %}
{% for p in pubs %}
  <article class="pub-card">
    <h3 class="pub-title">
      {% assign link = p.url | default: p.doi | default: p.arxiv | default: nil %}
      {% if link %}<a href="{{ link }}" target="_blank" rel="noopener">{{ p.title }}</a>{% else %}{{ p.title }}{% endif %}
    </h3>

    <p class="pub-authors">{{ p.authors | replace: me, me_bold }}</p>
    <p class="pub-venue">{% if p.type == 'journal' %}<strong>{{ p.venue }}</strong>{% else %}{{ p.venue }}{% endif %} ({{ p.year }})</p>

    <p class="badges">
      {% if p.doi %}<a href="{{ p.doi }}">DOI</a>{% endif %}
      {% if p.arxiv %}<a href="{{ p.arxiv }}">arXiv</a>{% endif %}
      {% if p.pdf %}<a href="{{ p.pdf }}">PDF</a>{% endif %}
      {% if p.code %}<a href="{{ p.code }}">Code</a>{% endif %}
    </p>

    {% if p.abstract %}<details><summary>Abstract</summary><p>{{ p.abstract }}</p></details>{% endif %}
    {% if p.bibtex %}<details><summary>BibTeX</summary><pre>{{ p.bibtex }}</pre></details>{% endif %}
  </article>
{% endfor %}
</div>
