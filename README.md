# HPSTR Pelican Theme

This is a port of the [HPSTR Theme](https://github.com/mmistakes/hpstr-jekyll-theme) to the [Pelican](https://github.com/getpelican/pelican) static site generator.

All credits for the initial Jekyll theme go to [Michael Rose](https://github.com/mmistakes)


## What HPSTR brings to the table:

* Responsive templates for post, page, and post index. Looks great on mobile, tablet, and desktop devices.
* Gracefully degrades in older browsers. Compatible with Internet Explorer 8+ and all modern browsers.
* Modern and minimal design.
* Sweet animated menu.
* Readable typography to make your words shine.
* Support for large images to call out your favorite posts.
* Social Sharing links for Facebook, Twitter, and Google+ if you choose to enable.
* [FontAwesome](http://fortawesome.github.io/Font-Awesome/) 4.1.0 ready. Include any of the [439 available icons](http://fortawesome.github.io/Font-Awesome/icons/) in your blog posts.
* Google Analytics
* Google Authorship, [OpenGraph](http://ogp.me/) and [Twitter Cards](https://dev.twitter.com/cards/overview) metadata for better SEO and sharing / distribution on social network plateforms
* Semantic information via rdfa-lite in article ([BlogPosting](http://schema.org/BlogPosting)) and page ([WebPage](http://schema.org/WebPage)) templates


## Supported plugins

Pelican blogging system comes with additional plugins that you can install and activate for your website. For more information see the [pelican-plugins](https://github.com/getpelican/pelican-plugins) repository.

Here are the plugins that should work out of the box with that theme if enabled:

* [related posts](https://github.com/getpelican/pelican-plugins/tree/master/related_posts)

    Displays related articles at the bottom of a blog post being read.

* [i18n subsites](https://github.com/getpelican/pelican-plugins/tree/master/i18n_subsites)

    Extends the translations functionality by creating internationalized sub-sites for the default site. Also takes care of translating theme items.


## Localization | Translation

This theme has some items / texts marked as localized in templates files. It relies on the [Jinja2 i18n extension] (http://jinja.pocoo.org/docs/templates/#i18n) to do the job and replace these texts with their translated couterparts in the appropriate language.

It means that you need to enable the jinja2.ext.i18n extension by adding the following line to your pelican configuration :
```python
JINJA_EXTENSIONS = ['jinja2.ext.i18n']
```

*THIS IS MANDATORY*, please don't skip this step otherwise you won't be able to generate the website.


### Add translations for a language

You downloaded this theme and love it but unfortunately your favorite language is not supported ?
-> *We need you !*

1. Please follow these [instructions](https://github.com/getpelican/pelican-plugins/blob/master/i18n_subsites/localizing_using_jinja2.rst) for how to translate template items
2. Make a pull request
3. Receive many thanks from the community :)


## Content license

You can optionally declare a [Creative Commons license](http://creativecommons.org) for the content of your site. It will appear in the site's footer. To enable, use one of the following two ways for configuration.

* To choose the license by name, set `CC_LICENSE` to the common abbreviated name of the license: `"CC-BY"` (require attribution), `"CC-BY-SA"` (require ShareAlike), `"CC-BY-ND"` (NoDerivatives) , `"CC-BY-NC"` (require attribution, no commercial reuse), `"CC-BY-NC-SA"` (require ShareAlike, no commercial reuse), or `"CC-BY-NC-ND"` (NoDerivatives, no commercial reuse).
* Alternatively, choose the licence by features:
 * `CC_LICENSE_DERIVATIVES` - `"yes"` if permitted, `"no"` if not permitted, and `"ShareAlike"` if derivatives must be shared under the same terms.
 * `CC_LICENSE_COMMERCIAL` - `"yes"` if commercial reuse is permitted, and `"no"` otherwise.
* Optionally, you can include attribution markup in the license mark by setting `CC_ATTR_MARKUP` to _True_.

The license choice mirrors the [Creative Commons License Chooser](http://creativecommons.org/choose/). Source for the macro that renders the mark is at http://github.com/hlapp/cc-tools.


## Footer

The footer will display a copyright message using the AUTHOR variable and the year of the latest post. If a content license mark is enabled (see above), that will be shown as well.


## Setup for an existing pelican website

1. Clone this theme into your pelican's site theme directory
2. Update your site ```pelicanconf.py``` configuration file

``` python
#!/usr/bin/env python
# -*- coding: utf-8 -*- #

from __future__ import unicode_literals

# Required as some texts in this theme templates are localized with gettext
JINJA_EXTENSIONS = ['jinja2.ext.i18n']

# User info
AUTHOR = u'Your name'
AUTHOR_ABOUT = u'Your bio goes here. It shouldn't be super long but a good two sentences or two should suffice.'

#  If not set, defaults to SITEURL/images/avatar.jpg
#  Do not include preceding /
AVATAR = 'static/images/avatar.png'


SITENAME = u'Site Title'
SITEURL = ''

# Directories configuration
PATH = 'content'
ARTICLE_PATHS = ['posts']

# Any extra files should be added here
STATIC_PATHS = [
    'extra',
    'images'
]

EXTRA_PATH_METADATA = {
    'extra/robots.txt': {'path': 'robots.txt'}
}

# By default we enable pretty highlighing in markdown:
MD_EXTENSIONS = ['codehilite(css_class=highlight)', 'extra', 'toc']

# Pagination
DEFAULT_PAGINATION = 3

# Categories
USE_FOLDER_AS_CATEGORY = False
DEFAULT_CATEGORY = 'Misc'

# Plugin path
PLUGIN_PATHS = ['../pelican-plugins']
PLUGINS = ['related_posts', 'sitemap', 'i18n_subsites']

# Theme
THEME = 'theme/pelican-hpstr'

# Theme options
BACKGROUND = 'bg_image.png'
ABOUT_PAGE = 'about.html'

# Blogroll / Links
LINKS = (('Pelican', 'http://getpelican.com/'),
         ('Python.org', 'http://python.org/'),
         ('Jinja2', 'http://jinja.pocoo.org/'),
         ('You can modify those links in your config file', '#'),)

# Social widgets
SOCIAL = (('github', 'https://github.com/yourname', 'GitHub'),
          ('twitter', 'http://twitter.com/yourname'),
          ('linkedin', 'http://fr.linkedin.com/in/yourname', 'LinkedIn'),)

# Social meta tags info
SOCIAL_META_ENABLED = True
SOCIAL_META = {
    'google': '<GOOGLE_ID>',
    'twitter': {
        'creator': '@creator_id'
        'site': '@site_id'
    }
}


# Sitemap configuration
SITEMAP = {
    'format': 'xml',
    'priorities': {
        'articles': 0.5,
        'indexes': 0.5,
        'pages': 0.5
    },
    'changefreqs': {
        'articles': 'weekly',
        'indexes': 'daily',
        'pages': 'monthly'
    }
}

# I18n
I18N_TEMPLATES_LANG = 'en'

```

3. Deployement specific configuration ```publishconf.py```

``` python
#!/usr/bin/env python
# -*- coding: utf-8 -*- #

# Enable google analytics
GOOGLE_ANALYTICS = "YOUR TRACKING ID"
```


## Questions / Requests ?

Having a problem getting something to work, have some questions or want an addition to this theme ?
Ping me on Twitter [@jonathan_dray](http://twitter.com/jonathan_dray) or [file a GitHub Issue](https://github.com/spiroid/pelican-hpstr/issues/new).


## License

As the original theme is licensed under the [GNU General Public License](https://github.com/mmistakes/hpstr-jekyll-theme/blob/master/LICENSE), i choose to distribute the Pelican version
under the same conditions.
This theme is free and open source software, distributed under the [GNU General Public License](https://github.com/spiroid/pelican-hpstr/blob/master/LICENSE) version 2 or later. So feel free to to modify this theme to suit your needs.
