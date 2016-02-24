---
title: Sw:ag Pages
---

The __swag/pages__ directory in the user's folder holds the files to be generated as pages of the final website.

The Sw:ag Generator will try to process every files located in the __swag/pages__ directory. Pages can be

* Templates: Twig files that are rendered and placed in the _destination_ folder
* Assets: Files of any nature like CSS, JS that are simply copied in the _destination_folder
* Skipped files: Either hidden files or non marked Twig files

## Twig Files

In order to be processed as pages for the generated website, Twig files need to start with a Sw:ag meta. The meta (which is a Twig comment) must contain the `generate: true` entry.

example of a Sw:ag meta for Twig files
```twig
{# meta
generate: true
#}
```

### Standalone Twig files

The meta shown above is all it needs to have you page processed. The page will be rendered via the Twig engine and placed in the destination directory matching the relative path to the `pages` directory.

If the destination directory is `static_website` and the Twig file path is `…/pages/team/members.html.twig`, the final processed file will be `…/static_website/team/members.html`.

### Iterative Twig files

Think of a blog articles… What if you could just generate articles with the same Twig template and get the contents from your data? Shouldn't it be great?

Well, Sw:ag can generate pages based on a single iterative Twig file upon info extracted from user's data.

To be rendered as an iterative template, the Sw:ag meta in the Twig file must contain the following info:
```
{# meta
generate: true      #
type:     iterative #
data:     posts     # path in the data variable
item:     post      # name of the item in this Twig template
#}
```

setting | role | required | default
--------|------|----------|--------
`generate` | marks the twig template as existing page for the generated website | optional | false
`type`     | states it needs to generate one page per item in the "posts" array | optional | false
`data`     | path in the data variable. It can be deep e.g blog.fr.posts        | required when type is iterative |
`item`     | name of the item in this Twig template i.e {{ post.title }}        | required when type is iterative |

Currently, the generated files are placed in the destination directory relatively to the Twig file location in the `pages` directory. The name of the file is the key of the data being processed suffixed by html.

## Assets

Every other files will just be copied from the `pages` directory to the destination directory. For example, `…/pages/css/style.css` will be duplicated to `…/static_website/css/style.css`.

## Skipped files

Some files are skipped by default:

* Twig files having no meta comment
* hidden files i.e. files whose name starts with a dot.
