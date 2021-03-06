OpenShift - Strapping-MediaWiki
===============================

This repository is designed to be used with http://openshift.redhat.com/
applications.  To use, just follow the quickstart below.


Quickstart
----------

1. Create an account at http://openshift.redhat.com/
2. Create a php-5.3 application and attach mysql to it:
<pre>
$ rhc app create -a strapping -t php-5.3
$ rhc cartridge add -a strapping -c mysql-5.1
</pre>
3. Clone your app repository:  
`rhc app show` gives you information about your app, including the git url 
<pre>
$ rhc app show -a strapping
$ git clone ssh://[uuid]@strapping-[namespace].rhcloud.com/~/git/strapping.git
</pre>
3. Add this upstream strapping-mediawiki repo
<pre>
$ cd strapping
$ git remote add upstream -m master git://github.com/EmilyDirsh/strapping-mediawiki-quickstart.git
$ git pull -s recursive -X theirs upstream master
</pre>
4. Then push the repo upstream
<pre>
$ git push
</pre>
5. That's it, you can now checkout your application at:
   `http://strapping-[namespace].rhcloud.com`
6. Default Admin Username: `Admin`  
   Default Password: `OpenShiftAdmin`

Updates
-------

In order to update or upgrade to the latest strapping-mediawiki-quickstart, you'll need to re-pull
and re-push.

1. Pull from upstream:
<pre>
$ cd strapping/
$ git pull -s recursive -X theirs upstream master
</pre>
2. Push the new changes upstream
<pre>
$ git push
</pre>

Repo layout
-----------

`php/` - Externally exposed php code goes here   
`libs/` - Additional libraries   
`misc/` - For not-externally exposed php code   
`../data` - For persistent data   
`deplist.txt` - list of pears to install   
`.openshift/action_hooks/build` - Script that gets run every push, just prior to starting your app   


Notes about layout
------------------

Please leave php, libs and data directories but feel free to create additional
directories if needed.

Note: Every time you push, everything in your remote repo dir gets recreated
please store long term items (like an sqlite database) in ../data which will
persist between pushes of your repo.


deplist.txt
-----------

A list of pears to install, line by line on the server.  This will happen when
the user git pushes.  


----------------------------------------------------------------------------------------------------------

Strapping-Mediawiki
===================

[strapping-mediawiki on GitHub] (https://github.com/OSAS/strapping-mediawiki)

Strapping is an elegant, responsive, and friendly starter skin for MediaWiki. Its purpose is to provide a good base to build upon, and was primarily created to provide a great default for wiki-as-a-website — but it works well for standard wikis too.

Strapping is built on top of a modified Vector theme from MediaWiki and utilizes Twitter's Bootstrap for base layout, typography, and additional widgets.

Because Strapping uses Bootstrap with its responsive extension, any site using this skin works well on desktop browsers and scales down to display beautifully on hand-held devices like tablets and smartphones.

Strapping also has complete coverage for all of MediaWiki, including the user preferences and admin pages. All of MediaWiki's features are included, too.

Customizing Strapping
---------------------

###Basic Bootstrap customization

Bootstrap has a customization page
where you can change several aspects of the Bootstrap theme.
Simply:

1. Visit [the Bootstrap customizer page](http://twitter.github.com/bootstrap/customize.html)
2. change values
3. click the giant button at the bottom of the page
4. replace Strapping's `bootstrap` directory with the one in your ZIP file

Note: Since Bootstrap is based on the LESS CSS preprocessor, you can also achieve similar results from a command line.

### Bootswatch

[Bootswatch](http://bootswatch.com/) is a project
that provides drop-in Bootstrap CSS replacements.

Visit the site and grab a theme to start using it immediately.


### theme.css

This method can be used without any other customizations,
or in addition to altering Bootstrap themes.

1. In the `screen.css` file, uncomment the `theme.css` import.
2. Add custom CSS to the `theme.css` file,
   including any colors and fonts you'd like to use.

### Font sources

Custom fonts can be found on [Google Web Fonts](http://google.com/webfonts)
and you can make your own `@font-face`-ready fonts
(if you have the permission to do so)
with [FontSquirrel's generator](http://fontsquirrel.com/fontface/generator)


Markup reference
----------------

While plain vanilla MediaWiki markup can be used,
sites using Strapping can also utilize any of Bootstrap's CSS
for more advanced layout and markup.

Layout
------

Do **NOT** use tables for layout.
Instead, use Bootstrap's scaffolding to do layout. 

Bootstrap scaffolding is based on having rows
that are formed with 12 possible columns.
To span a column, you use a classname of `span`
plus the number of columns you'd like to span,
such as `span2` to use up 2 columns.
Everything should add up to 12
(or less, if there's going to be space on the right side).

Make sure to wrap the spans into `row`s for everything to work correctly.

It looks something like this:

```html
<div class="row">
  <div class="span6"></div>
  <div class="span6"></div>
</div>
<div class="row">
  <div class="span6 offset2"></div>
  <div class="span3"></div>
  <div class="span1"></div>
</div>
```

For more information,
please visit [Bootstrap's documentation](http://twitter.github.com/bootstrap/scaffolding.html).

Documentation
-------------

Please consult [MediaWiki's formatting page](http://www.mediawiki.org/wiki/Help:Formatting)
for help with writing wiki text.

If you're feeling adventurous and want to use some more advanced formatting,
you can attach any Bootstrap classes to `div`s.


Licensing, Copying, Usage
-------------------------

Strapping is open source, and built on open source projects.

Please check out the [LICENSE file](https://github.com/OSAS/strapping-mediawiki/blob/master/LICENSE) for details.


