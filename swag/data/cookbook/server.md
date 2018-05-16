<h2><span>A quick server for your generated pages</span></h2>

You can quickly start a PHP web server that can serve your generated files through a http connection.

Displaying the file directly from your file system is easier but can break links (relative and absolute). Javascript has some limitations as well.

### Starting the webserver

In your terminal, being located in the folder containing both the source and default destination folder, just type the following command:

<div class="row">
    <div class="col-sm-12" markdown="1">
```shell
php -S localhost:8000 -t ./web
```
    </div>
</div>

You can now reach your pages with any browser at the following address: <a href="http://localhost:8000">http://localhost:8000</a>

More about [configuring a PHP webserver](http://php.net/manual/fr/features.commandline.webserver.php)!
