---
title: Unknown Bimil
layout: home
permalink: /
---

<div class="hero">
  <p class="hero-eyebrow">몰랩 비밀 리서치 셀</p>
  <h1>어둠 속에서 추출한 인사이트를 이곳에 기록합니다.</h1>
  <p class="hero-body">
    김원일 비밀 수행부서는 로열블루의 맥박으로 최신 전략, 데이터, 심리·기술 실험을 정리합니다.
    대표님이 바로 전선으로 투입할 수 있는 형태로 지식을 다듬습니다.
  </p>
  <div class="hero-actions">
    <a class="btn btn-primary" href="#recent">최신 보고서 보기</a>
    <a class="btn btn-ghost" href="{{ '/about/' | relative_url }}">프로토콜 살펴보기</a>
  </div>
</div>

## 최근 보고서
<div class="recent-reports" id="recent">
{% assign latest_posts = site.posts | sort: 'date' | reverse | slice: 0, 4 %}
{% for post in latest_posts %}
  {% assign category_line = post.categories | join: ', ' %}
  {% if category_line == '' and post.category %}
    {% assign category_line = post.category %}
  {% endif %}
  {% assign excerpt_text = post.excerpt | strip_html | strip %}
  {% if excerpt_text == '' %}
    {% assign excerpt_text = '요약 문장은 준비 중입니다. 세부 내용을 직접 확인해 주세요.' %}
  {% endif %}
  <article class="report-card">
    <p class="report-meta">{{ post.date | date: "%Y.%m.%d" }} • {{ category_line | default: '분류 미정' }}</p>
    <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
    <p class="report-excerpt">{{ excerpt_text | truncate: 110 }}</p>
    <a class="report-link" href="{{ post.url | relative_url }}">상세 리포트 →</a>
  </article>
{% endfor %}
</div>

## 카테고리
<div class="category-grid">
{% for category in site.categories %}
  {% assign name = category[0] %}
  {% assign posts = category[1] %}
  <a class="category-card" href="{{ '/category/' | append: name | relative_url }}">
    <span class="label">{{ name }}</span>
    <span class="count">{{ posts | size }} docs</span>
  </a>
{% endfor %}
</div>
