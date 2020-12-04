---
title: Current App Testers
icon: fas fa-tags
order: 2

# All the Tags of posts.
# v2.0
# https://github.com/cotes2020/jekyll-theme-chirpy
# © 2017-2019 Cotes Chung
# MIT License
---

## **Getting Started**

#### **Getting access to the app**

Contact Dhaval Parmar either via Slack or email <dhavalparmar@northeastern.edu> to get access. You will need to provide your Google ID (for Android) 
or Apple ID (for iOS) to be added as a tester.

*Please let Dhaval know which phone make/model you are using to test the app or add yourself to this document [here](https://docs.google.com/spreadsheets/d/1hu2XE6cPSM1YHxyi2hRoknW_9eZPqcXMEk7_ImjYQZs/edit#gid=0).**

#### **Downloading the test app**

###### **Android**
Once you have been added as a testor, you may go to the following link to download and install the app: <https://play.google.com/apps/internaltest/4700153961691507100> 

###### **iPhone**
Once you have been added as a testor, you will receive an invitation to download and install the app via email, with the subject 
"Evelyne Kimani has invited you to test the SCC Church Connect app".
Apps that are in the testing stage are installed through another app called TestFlight. The invitation email will have an
access code which you will need to enter into TestFlight.

#### **Log-in information for the app**

Username: Your first name
Password: 12345

## **How to report bugs**


## **Questions, Concerns, Comments?**

If you have any questions or concerns about the project, please contact the Principal Investigator: Timothy Bickmore at 617-373-5477

{% comment %}
  'site.tags' looks like a Map, e.g. site.tags.MyTag.[ Post0, Post1, ... ]
  Print the {{ site.tags }} will help you to understand it.
{% endcomment %}
<div id="tags" class="d-flex flex-wrap ml-xl-2 mr-xl-2">
{% assign tags = "" | split: "" %}
{% for t in site.tags %}
  {% assign tags = tags | push: t[0] %}
{% endfor %}

{% assign sorted_tags = tags | sort_natural %}

{% for t in sorted_tags %}
  <div>
    <a class="tag" href="{{ site.baseurl }}/tags/{{ t | replace: ' ', '-' | downcase | url_encode }}/">{{ t }}<span class="text-muted">{{ site.tags[t].size }}</span></a>
  </div>
{% endfor %}

</div>
