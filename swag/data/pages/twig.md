<h2><span>Twig files</span></h2>

<div class="row">
    <div class="col-md-6" markdown="1">
In order to be processed as pages for the generated website, Twig files need to start with a Sw:ag meta. The meta (which is a Twig comment) must contain the `generate: true` entry.
    </div>
    <div class="col-md-6" markdown="1">
<div class="pre-caption">example of a Sw:ag meta for Twig files</div>
```twig
{# meta
generate: true
#}
```
    </div>
</div>


### Standalone Twig files

The meta shown above is all it needs to have you page processed. The page will be rendered via the Twig engine and placed in the destination directory matching the relative path to the __pages__ directory.

If the Twig file path is __pages/team/members.html.twig__, the final processed file will be __static_website/team/members.html__.

### Iterative Twig files
_Sw:ag_ can batch pages based on a single iterative Twig file upon info extracted from [user's data](data.html).

<div class="row">
    <div class="col-sm-6" markdown="1">
To be rendered as an iterative template, the Twig file must be marked with a _Sw:ag_ meta as follows:
    </div>
    <div class="col-sm-6" markdown="1">
<div class="pre-caption">Sw:ag meta triggering an iterative Twig processing</div>
```
{# meta
generate: true
type:     iterative
data:     posts
item:     post
#}
```
    </div>
</div>



<div class="setting-table" markdown="1">
setting | role | required | default
--------|------|----------|--------
`generate` | marks the twig template as existing page for the generated website | optional | false
`type`     | states it needs to generate one page per item in the "posts" array | optional | false
`data`     | path in the data variable. It can be deep e.g blog.fr.posts        | required when type is iterative |
`item`     | name of the item in this Twig template i.e {{ post.title }}        | required when type is iterative |
</div>

Currently, the generated files are placed in the __static_website__ directory relatively to the Twig file location in the __pages__ directory. The name of the file is the key of the data being processed suffixed by html.
