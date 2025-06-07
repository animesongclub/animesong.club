---
layout: default
title: 東京のアニソンDJ店舗一覧
---

<h1>東京のアニソンDJ店舗</h1>

<p>東京エリアにある{{ site.data.venues.tokyo.size }}件のアニソンDJ店舗情報です。</p>

<div class="venue-list">
  {% for venue in site.data.venues.tokyo %}
  <div class="venue-card">
    <div class="venue-image">
      <img src="{{ '/assets/images/' | append: venue.image | relative_url }}" alt="{{ venue.name }}">
    </div>
    <div class="venue-info">
      <h3><a href="{{ '/venues/' | append: venue.id | relative_url }}">{{ venue.name }}</a></h3>
      <p class="venue-region">東京</p>
      <p>{{ venue.description }}</p>
      {% if venue.events %}
      <div class="venue-events">
        <h4>開催イベント</h4>
        {% for event in venue.events %}
        <div class="event">
          <p class="event-name">{{ event.name }}</p>
          {% if event.organizer %}
          <p class="event-organizer">主催: {{ event.organizer }}</p>
          {% endif %}
          <p>{{ event.description }}</p>
          {% if event.day != "イベントスケジュールによる" %}
          <p><strong>開催日:</strong> {{ event.day }}</p>
          {% endif %}
          {% if event.time != "イベントスケジュールによる" %}
          <p><strong>時間:</strong> {{ event.time }}</p>
          {% endif %}
        </div>
        {% endfor %}
      </div>
      {% endif %}
      <p><strong>住所:</strong> {{ venue.address }}</p>
      <p><strong>営業時間:</strong> {{ venue.hours }}</p>
      <p><a href="{{ '/venues/' | append: venue.id | relative_url }}" class="button">詳細を見る</a></p>
    </div>
  </div>
  {% endfor %}
</div>

<div class="map-container">
  <h2>東京のアニソン店舗マップ</h2>
  <iframe
    width="100%"
    height="450"
    style="border:0"
    loading="lazy"
    allowfullscreen
    src="https://www.google.com/maps/embed/v1/search?key=YOUR_API_KEY&q=アニソン+バー+東京">
  </iframe>
  <p class="map-note">※ 実際のAPI keyに置き換えてください。</p>
</div>

<div class="back-to-top">
  <a href="{{ '/' | relative_url }}">&laquo; トップページに戻る</a>
</div>
