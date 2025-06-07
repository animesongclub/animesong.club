---
layout: default
title: 大阪のアニソンDJ店舗一覧
---

<h1>大阪のアニソンDJ店舗</h1>

<p>大阪エリアにある{{ site.data.venues.osaka.size }}件のアニソンDJ店舗情報です。</p>

<div class="venue-list">
  {% for venue in site.data.venues.osaka %}
  <div class="venue-card">
    <div class="venue-image">
      <img src="{{ '/assets/images/' | append: venue.image | relative_url }}" alt="{{ venue.name }}">
    </div>
    <div class="venue-info">
      <h3><a href="{{ '/venues/' | append: venue.id | relative_url }}">{{ venue.name }}</a></h3>
      <p class="venue-region">大阪</p>
      <p>{{ venue.description }}</p>
      <p><strong>住所:</strong> {{ venue.address }}</p>
      <p><strong>営業時間:</strong> {{ venue.hours }}</p>
      <p><a href="{{ '/venues/' | append: venue.id | relative_url }}" class="button">詳細を見る</a></p>
    </div>
  </div>
  {% endfor %}
</div>

<div class="map-container">
  <h2>大阪のアニソン店舗マップ</h2>
  <iframe
    width="100%"
    height="450"
    style="border:0"
    loading="lazy"
    allowfullscreen
    src="https://www.google.com/maps/embed/v1/search?key=YOUR_API_KEY&q=アニソン+バー+大阪">
  </iframe>
  <p class="map-note">※ 実際のAPI keyに置き換えてください。</p>
</div>

<div class="back-to-top">
  <a href="{{ '/' | relative_url }}">&laquo; トップページに戻る</a>
</div>
