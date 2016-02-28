<h2><span>pages directory</span></h2>

<div class="row">
    <div class="col-sm-12" markdown="1">
The structures of the __pages__ and __static_website__ directories are very similar.
    </div>
</div>

<div class="row">
    <div class="col-sm-5">
<pre>
📁 pages
│
├──❌ .hidden_file
├──📁 blog
│   ├──📁 post
│   │   └──🔃 article.html.twig
│   └──❗️index.html.twig
├──⭕️base.html.twig
├──⭕️header.html.twig
├──❗️contact.html.twig
├──❗️index.html.twig
├──📁 style
│   ├──📁 css
│   │   └──❕main.css
│   └──📁 js
│       └──❕app.js
…
</pre>
    </div>

    <div class="col-sm-2 text-center">
        <span class="processing-arrow">➡︎</span>
    </div>

    <div class="col-sm-5">
<pre>
📁 static_website
│
├──📁 blog
│   ├──📁 post
│   │   ├──📄 post_1.html
│   │   ├──…
│   │   └──📄 post_n.html
│   └──📄 index.html
├──📄contact.html
├──📄index.html
├──📁 style
│   ├──📁 css
│   │   └──📄main.css
│   └──📁 js
│       └──📄app.js
…
</pre>
    </div>
</div>

<div class="row">
    <div class="col-sm-12">
    <pre>❗️Twig marked for processing   🔃 Twig marked as iterative   ⭕️ Twig not marked   ❕Asset to copy   ❌ Ignored file</pre>
    </div>
</div>

[More about pages configuration…](pages.html)
