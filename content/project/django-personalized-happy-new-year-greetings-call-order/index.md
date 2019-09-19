---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "New Year's Miracle"
summary: "A Django site built from scratch"
authors: []
tags: ['python', 'django', 'postresql', 'celery', 'redis', 'UWSGI', 'docker', 'nginx', 'Jinja2', 'web']
categories: []
date: 2019-01-01T22:04:25+03:00

# Optional external URL for project (replaces project detail page).
external_link: ""

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: "Django Personalized Happy New Year Greetings Call Order Received"
  focal_point: ""
  preview_only: true

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
links:
- name: New Year's Miracle personalized Happy New Year greetings service
  url: https://zvonok.novogodnee-chudo.ru/
  icon_pack: fas
  icon: external-link-alt

- name: A WayBack Archive copy of New Year's Miracle site
  url: https://web.archive.org/web/20190918211522/https://zvonok.novogodnee-chudo.ru/
  icon_pack: fas
  icon: history

url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

I developed the site of “New Year's Miracle” project. It was a Django powered site (built from scratch) to collect orders for personalized Happy New Year greetings. 

I used Jinja 2 templates to put Django install front-end assets given as HTML, CSS, JavaScript bundle.

For storage on site I used PostreSQL DB 10. Delayed jobs as email sending, calling was done using Celery queue and Redis Storage.

I created a Docker container with UWSGI + Django for deployment on Nginx web server, and tested this container works on 38 core bare metal configuration.

{{< figure src="featured.png" title="Screenshot of call order received" lightbox="true" >}}

{{< figure src="Django Personalized Happy New Year Greetings Call Order CMS Admin.png" title="Screenshot of Django admin view" lightbox="true" >}}

Service description below I took from Russian resource for parents [www.ya-roditel.ru direct link](https://www.ya-roditel.ru/national-campaign/news/v-etom-godu-6637/) 

It is Google translated to English. 

> As part of the “New Year's Miracle” project, a unique service of free personalized phone call from Santa Claus began its work. Previously, parents can choose not only a name, but also an individual instruction to the child from Santa Claus.

> “Hot lines” of Santa Claus have been working for more than a year, but, as a rule, they mean receiving incoming calls and playing out non-personalized greetings. For the first time in history, the new service will allow you to receive a personalized call from the main New Year wizard. Having picked up the phone, the child will hear his name 5 times, and if at the same time he needs to be more attentive to his studies or not to refuse vegetables at dinner, Grandfather will definitely say so in his congratulation. Parents choose a convenient date and time for the call on their own - the coveted call can be heard at least five minutes after the application has been left.

> In addition, if the child has a brother or sister, congratulations will be addressed to both of them. A one-time congratulation is also provided for three children.

> The project manager Maxim Shuvaev noted that over the last 7 days of December it is planned to make up to a million calls, but so far only in Russia. In the future, it is planned to connect to the shares of other CIS countries.