## data directory

Sw:ag generates a structured data based on the `data` directory tree.

<div class="row">
    <div class="col-sm-5">
The following organization

<pre>
📁 swag
│
├──📁 data
│   ├──📁 posts
│   │  ├──📄 post_1.md
│   │  ├──…
│   │  └──📄 post_n.md
│   └──📄 site.yml
…
</pre>
    </div>

    <div class="col-sm-2 text-center">
        <span class="processing-arrow">➡︎</span>
    </div>

    <div class="col-sm-5">
    will generate the following data:
<pre>
data:
    site:
        url: myurl.com
        title: My generated website
        …
    posts:
        post_1:
            author:  Jane Doe
            date:    2016-12-01
            content: An awesome post… chit-chat
        …
        post_n:
            author:  Max Cool
            date:    2016-06-22
            content: Another article… chit-chat
</pre>
    </div>
</div>
