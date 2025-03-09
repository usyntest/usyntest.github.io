---
layout: page
title: GGS Social
description: Created a college social media platform using Python (Django) and TailwindCSS and deployed it.
importance: 1
# category: work
---

#### Overview

**GGS Social** is a dedicated college **social media platform** developed using `Django` for the backend and `TailwindCSS` for the frontend. This platform aims to foster community engagement within a college environment by providing features tailored to the needs of students and faculty.

##### Key Features:

- **User Authentication**: Secure registration and login functionalities to ensure a safe user environment.
- **Profile Management**: Allows users to create and manage their profiles, including personal information and profile pictures.
- **Post Creation and Interaction**: Users can create posts, share updates, and engage with others through comments and likes.
- **Responsive Design**: Ensures optimal viewing and interaction experiences across a wide range of devices.

##### Technical Highlights:

- **Backend Architecture**: Designed using `Django`, focusing on scalability and maintainability.
- **Database Models**: Structured to efficiently handle user data, posts, and interactions.
- **Frontend Development**: Utilized `TailwindCSS` to create a responsive and modern user interface.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ggs-social-ui-1.jpg" title="search screen for mojster" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ggs-social-ui-2.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ggs-social-ui-3.jpg" title="search screen for mojster" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ggs-social-ui-4.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ggs-social-ui-5.jpg" title="search screen for mojster" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ggs-social-ui-6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

#### Technologies Used
- **Frontend**: HTML5, CSS3, JavaScript, TailwindCSS
- **Backend**: Python (Django)
- **Database**: SQLite

#### How to Use
Installation  

```bash
git clone https://github.com/usyntest/ggs-social.git
cd ggs-social
pip install -r requirements.txt
```

Make tables 
```bash
python manage.py makemigrations
python manage.py migrate
```

Running the server
```bash
python manage.py runserver
```

#### Links

- 📂 [GitHub Repository](https://github.com/usyntest/ggs-social)