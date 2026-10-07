---
layout: default
title: About
permalink: /about/
---

<section class="wrap page-about">
  <div class="section-head">
    <span class="section-index">01</span>
    <h1>About</h1>
  </div>
  <div class="prose">
    {% capture about %}{% include about.md %}{% endcapture %}
    {{ about | markdownify }}
  </div>
</section>
