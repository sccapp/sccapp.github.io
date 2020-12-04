---
title: Progress So Far
icon: fas fa-stream
order: 1

# All the Categories of posts
# v2.0
# https://github.com/cotes2020/jekyll-theme-chirpy
# © 2017-2019 Cotes Chung
# MIT License
---
## Summary of the Work in Year 1 

##### **Project Goal:**
The goal of the project is to expand church-based health promotion activities. We partnered with the Black Ministerial Alliance (BMA) 
in Boston and church members to co-design a smartphone application. By working with church members, we hope to create an application that 
reflects the priorities and values of their church community. 

##### Members from the two churches have participated in:


##### **9** different types of sessions to design the app.
##### **40** total focus groups and interviews.

##### For a total of **62** hours on the project so far.

##### *Thank you so much for all your hard work this past year, and for sharing your experiences and insights with us!* 

![image](https://user-images.githubusercontent.com/75331796/101180473-a1b4e000-3619-11eb-9529-84d28ad54f3f.png)

## **Takeaways:**

With the help of church members, we identified four health topics: 

**Physical Activity, Nutrition, Stress and Mental Health, and Healthy Relationships.** 

We learned from church members that it is important that the application: 

- Promote in-person interactions and increase communication between church members.
- Support the user’s faith practices. 
- Reflect the diversity of the church communities. 

## **Next Steps:**

- **Building app prototypes.** We plan to build a series of app prototypes to be tested by members of your church community. 
- **Collaborating with Church Leaders.** 
- **Recruiting more Churches.**

## **Interested in Getting Involved?**
Contact us.

## **Questions, Concerns, Comments?**
Contact us.



{% assign HEAD_PREFIX = "h_" %}
{% assign LIST_PREFIX = "l_" %}

{% assign group_index = 0 %}

{% assign sort_categories = site.categories | sort %}

{% for category in sort_categories %}
  {% assign category_name = category | first %}
  {% assign posts_of_category = category | last %}
  {% assign first_post = posts_of_category | first %}

  {% if category_name == first_post.categories[0] %}
    {% assign sub_categories = "" | split: "" %}

    {% for post in posts_of_category %}
      {% assign second_category = post.categories[1] %}
      {% if second_category %}
        {% unless sub_categories contains second_category %}
          {% assign sub_categories = sub_categories | push: second_category %}
        {% endunless %}
      {% endif %}
    {% endfor %}

    {% assign sub_categories = sub_categories | sort %}
    {% assign sub_categories_size = sub_categories | size %}

  <div class="card categories">
    <!-- top-category -->
    <div class="card-header d-flex justify-content-between hide-border-bottom"
        id="{{ HEAD_PREFIX }}{{ group_index }}">
      <span>
      {% if sub_categories_size > 0 %}
        <i class="far fa-folder-open fa-fw"></i>
      {% else %}
        <i class="far fa-folder fa-fw"></i>
      {% endif %}
        <a href="{{ site.baseurl }}/categories/{{ category_name | replace: ' ', '-' | downcase | url_encode }}/"
          class="ml-1 mr-2">
          {{ category_name }}
        </a>

        <!-- content count -->
        {% assign top_posts_size = site.categories[category_name] | size %}
        <span class="text-muted small font-weight-light">
          {% if sub_categories_size > 0 %}
            {{ sub_categories_size }}
            {% if sub_categories_size > 1 %}categories{% else %}category{% endif %},
          {% endif %}
            {{ top_posts_size }}
            post{% if top_posts_size > 1 %}s{% endif %}
        </span>
      </span>

      <!-- arrow -->
      {% if sub_categories_size > 0%}
      <a href="#{{ LIST_PREFIX }}{{ group_index }}" data-toggle="collapse" 
        aria-expanded="true" aria-label="{{ HEAD_PREFIX }}{{ group_index }}-trigger" 
        class="category-trigger hide-border-bottom">
        <i class="fas fa-fw fa-angle-down"></i>
      </a>
      {% else %}
      <span data-toggle="collapse" class="category-trigger hide-border-bottom disabled">
        <i class="fas fa-fw fa-angle-right"></i>
      </span>
      {% endif %}

    </div> <!-- .card-header -->

    <!-- Sub-categories -->
    {% if sub_categories_size > 0 %}
    <div id="{{ LIST_PREFIX }}{{ group_index }}" class="collapse show" aria-expanded="true">
      <ul class="list-group">
        {% for sub_category in sub_categories %}
        <li class="list-group-item">
          <i class="far fa-folder fa-fw"></i>
          <a href="{{ site.baseurl }}/categories/{{ sub_category | replace: ' ', '-' | downcase | url_encode }}/"
            class="ml-1 mr-2">{{ sub_category }}</a>
          {% assign posts_size = site.categories[sub_category] | size %}
          <span class="text-muted small font-weight-light">{{ posts_size }}
            post{% if posts_size > 1 %}s{% endif %}
          </span>
        </li>
        {% endfor %}
      </ul>
    </div>
    {% endif %}

  </div> <!-- .card -->

    {% assign group_index = group_index | plus: 1 %}

  {% endif %}
{% endfor %}
