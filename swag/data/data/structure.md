<h2><span>the data tree</span></h2>

Every files located in the __swag/data__ directory will be processed. Each file will be added to the data tree. The name of the file just defines the key and its content becomes the value. Directories are treated in the same way except that the generated value is a subtree of key/value, and so on and on…

Eventually, the whole data set is injected in each handled Twig file during the pages generation.

### Example

<div class="row">
    <div class="col-sm-6">
        <p>The following yml file</p>
    </div>

    <div class="col-sm-6" markdown="1">
    <div class="pre-caption">data.site.yml</div>
```yml
---
url:     mywebsite.com
title:   My Awesome Website
charset: utf-8
```
    </div>
</div>

<div class="row">
    <div class="col-sm-6" markdown="1">
<p markdown="1">will generate the final `$data` variable.</p>
    </div>

    <div class="col-sm-6" markdown="1">
    <div class="pre-caption">generated $data</div>
```php
$data = [
    'site' => [
        'url'     => 'mywebsite.com',
        'title'   => 'My Awesome Website',
        'charset' => 'utf-8'
    ]
];
```
    </div>
</div>

<div class="row">
    <div class="col-sm-6" markdown="1">
<p markdown="1">Eventually, the data is accessible in the Twig templates.</p>
    </div>

    <div class="col-sm-6" markdown="1">
    <div class="pre-caption">Usecase in a Twig template</div>
```Twig
<!DOCTYPE html>
<html>
  <head>
    <meta charset="{{ site.charset }}">
    <title>{{ site.title }}</title>
  </head>
  <body>
    {% block body %}{% endblock %}
  </body>
</html>
```
    </div>
</div>

### Yml files

Yml is the more human friendly file format to store values. Its comprehensive syntax makes it easy to read but also to write.

### Markdown files

[Markdown](https://en.wikipedia.org/wiki/Markdown) is a lightweight markup language […] designed so that it can be converted to HTML. It allows to write HTML-ish files in a more readable (and human) way.

_Sw:ag_ handles Markdown files in a singular way compared to other data files. They can contain a meta data section delimited by triple dashes. Meta data will be extracted from the file and added to the `$data` tree. Like any other data files, the name of the file sets the key name. The value is a special data store containing meta in direct access as well as the content of the initial Markdown file.

<div class="row">
    <div class="col-sm-6" markdown="1">
<p markdown="1">A typical blog post written in Markdown like this.</p>
    </div>

    <div class="col-sm-6" markdown="1">
    <div class="pre-caption">2016-12-05-my-first-post.md</div>
```markdown
---
title:  my first blog post
author: The invisible man
date:   2016-12-05
tags:
  - web
  - static generator
---

# My First Blog Post

## Speaking out my passion
- A great topic
- You can't miss it
…
```
    </div>
</div>

<div class="row">
    <div class="col-sm-6" markdown="1">
will be handled in a Twig template the following way.

The content of the initial markdown file is simply injected in the final HTML by calling
`{{ post }}` in the Twig template.
    </div>

    <div class="col-sm-6" markdown="1">
    <div class="pre-caption">blog/article.html.twig</div>
```Twig
{# meta
generate: true
type:     iterative
data:     posts
item:     post
#}

{% extends 'base.html.twig' %}

{% block body %}
<article>
   <h1>{{ post.title }}</h1>
   <h2>
     <span class="author">{{ post.author }}</span>
     {{ post.date }}
   </h2>
   <div class="content">
     {{ post }} # the markdown content
   </div>
   <ul>
     {% for tag in post.tags %}
       <li>{{ tag }}</li>
     {% endfor %}
   </ul>
</article>
{% endblock %}

```
    </div>
</div>
