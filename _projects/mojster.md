---
layout: page
title: Mojster
description: A real-time analytics dashboard for monitoring content trends and user engagement on the Moj platform.
importance: 1
# category: work
---

#### Overview
Mojster is a real-time analytics dashboard designed to track content trends and user engagement on the Moj platform. By reverse-engineering Moj's API, it provides valuable insights into video content, language distribution, and trending hashtags.

Due to the lack of public API for the platform, I had to reverse engineer Moj's API using networking tools like `mitmproxy` and `wireguard`. Found all the endpoints to scrape the data from the platform.

Used `async` programming to make API calls to Moj faster and fetch all the data for the dashboard in real-time.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/mojster-ui-1.jpg" title="search screen for mojster" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/mojster-ui-2.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

#### Technologies Used
- **Frontend**: HTML5, CSS3, JavaScript, TailwindCSS
- **Charts**: Chart.js  
- **Backend**: Python (Flask)
- **Data Source**: Reverse-engineered Moj API for real-time data fetching 
- **Developer Tools**: mitmproxy, wireguard

#### How to Use
Installation  

```bash
git clone https://github.com/usyntest/mojster.git
cd mojster
pip install -r requirements.txt
```

Running the server
```bash
python -m flask --app server run
```

#### Links

- 📂 [GitHub Repository](https://github.com/usyntest/mojster)