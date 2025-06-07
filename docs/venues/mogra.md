---
layout: default
title: MOGRA - アニソンクラブ情報
---

<div class="venue-detail">
  <h1>{{ site.data.venues.tokyo[0].name }}</h1>
  
  <div class="venue-header">
    <div class="venue-image">
      <img src="{{ '/assets/images/' | append: site.data.venues.tokyo[0].image | relative_url }}" alt="{{ site.data.venues.tokyo[0].name }}">
    </div>
    <div class="venue-info">
      <p class="venue-region">東京</p>
      <p>{{ site.data.venues.tokyo[0].description }}</p>
    </div>
  </div>

  <div class="venue-section">
    <h2>基本情報</h2>
    <table class="venue-details">
      <tr>
        <th>名称</th>
        <td>{{ site.data.venues.tokyo[0].name }}</td>
      </tr>
      <tr>
        <th>住所</th>
        <td>{{ site.data.venues.tokyo[0].address }}</td>
      </tr>
      <tr>
        <th>ウェブサイト</th>
        <td><a href="{{ site.data.venues.tokyo[0].website }}" target="_blank" rel="noopener">{{ site.data.venues.tokyo[0].website }}</a></td>
      </tr>
      <tr>
        <th>営業時間</th>
        <td>{{ site.data.venues.tokyo[0].hours }}</td>
      </tr>
      <tr>
        <th>チャージ</th>
        <td>{{ site.data.venues.tokyo[0].cover }}</td>
      </tr>
    </table>
  </div>

  <div class="venue-section">
    <h2>イベント情報</h2>
    <div class="events-list">
      {% for event in site.data.venues.tokyo[0].events %}
      <div class="event-card">
        <h3>{{ event.name }}</h3>
        {% if event.organizer %}
        <p class="event-organizer"><strong>主催:</strong> {{ event.organizer }}</p>
        {% endif %}
        <div class="event-details">
          {% if event.day != "イベントスケジュールによる" %}
          <p><strong>開催日:</strong> {{ event.day }}</p>
          {% else %}
          <p><strong>開催日:</strong> 公式サイト・SNSでご確認ください</p>
          {% endif %}
          
          {% if event.time != "イベントスケジュールによる" %}
          <p><strong>時間:</strong> {{ event.time }}</p>
          {% else %}
          <p><strong>時間:</strong> 公式サイト・SNSでご確認ください</p>
          {% endif %}
        </div>
        <p class="event-description">{{ event.description }}</p>
        
        {% if event.name == "アニソンMatrix" %}
        <div class="featured-event">
          <p><strong>アニソンMatrix</strong>はMOGRA設立初期から続く伝統的なアニソンイベントです。DJさーや（SAAYA）さんによって主催されています。最新のイベント情報は公式サイトやSNSでご確認ください。</p>
        </div>
        {% endif %}
      </div>
      {% endfor %}
    </div>
  </div>

  <div class="venue-section">
    <h2>アクセス</h2>
    <div class="map">
      <iframe
        width="100%"
        height="450"
        style="border:0"
        loading="lazy"
        allowfullscreen
        src="https://www.google.com/maps/embed/v1/place?key=YOUR_API_KEY&q={{ site.data.venues.tokyo[0].name }}+{{ site.data.venues.tokyo[0].address | url_encode }}">
      </iframe>
    </div>
  </div>

  <div class="back-to-region">
    <a href="{{ '/regions/tokyo/' | relative_url }}">&laquo; 東京の店舗一覧に戻る</a>
  </div>
</div>

<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "MusicVenue",
  "name": "{{ site.data.venues.tokyo[0].name }}",
  "description": "{{ site.data.venues.tokyo[0].description }}",
  "address": {
    "@type": "PostalAddress",
    "addressCountry": "JP",
    "addressRegion": "東京都",
    "addressLocality": "渋谷区",
    "streetAddress": "宇田川町10-5 野村ビル B1F"
  },
  "url": "{{ site.data.venues.tokyo[0].website }}",
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": {{ site.data.venues.tokyo[0].coordinates.lat }},
    "longitude": {{ site.data.venues.tokyo[0].coordinates.lng }}
  },
  "event": [
    {% for event in site.data.venues.tokyo[0].events %}
    {
      "@type": "MusicEvent",
      "name": "{{ event.name }}",
      "description": "{{ event.description }}"{% if event.organizer %},
      "organizer": {
        "@type": "Person",
        "name": "{{ event.organizer }}"
      }{% endif %}
    }{% unless forloop.last %},{% endunless %}
    {% endfor %}
  ]
}
</script>
