---
layout: post
title: "pagination in jekyll steps"
tag-name: jekyll
---
ok, this is a stupid meta-post about me fiddling around with jekyll.

i got pagination to work, and it wasn't well documented on the [jekyll site](https://jekyllrb.com/docs/pagination/).

here's what i had to do:
- first, needed to add the gem to my <code>gemfile</code>: <code>gem "jekyll-paginate", "~> 1.1"</code>
- if you haven't yet, stop here and run <code>bundle install</code> to make sure you've got the right gems installed.
- next, needed to modify the <code>_config.yml</code>: 
<pre>plugins:
    - jekyll-paginate

paginate: 5</pre>
- if you stop here, things will be working properly, but you'll probably get an error about the lack of index.html file to paginate against.
- next, you need to create an <code>index.html</code> file in the main root of your blog. this file will then need to use the </code>paginator</code> code you can find on the [jekyll site](https://jekyllrb.com/docs/pagination/).
- i had to stop using <code>index.md</code> that referred to a <code>home.html</code> template, and instead move most of the template code into my index.html file.
- i also had to add some stupid control logic to the <code>header.html</code> include file i am using to make sure it didn't put "home" in the header 3 times (one for each pagination, i think). here's what i did in all of its shitty glory: 
<code>{%raw%}
{%- if my_page.title -%}
  {%- if my_page.title != "home" or my_page.title == 'home' and home_count == 0 -%}
  <a class="page-link" href="{{ my_page.url | relative_url }}">{{ my_page.title | escape }}</a>
  {%- endif -%}
  {%- if my_page.title == "home" -%}
    {%- assign home_count = 1 -%}
  {%- endif -%}
{%- endif -%}
{%endraw%}</code>
