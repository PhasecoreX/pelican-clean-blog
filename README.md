# Pelican Clean Blog Theme

Theme based on [Clean Blog layout](http://ironsummitmedia.github.io/startbootstrap-clean-blog/).

## Screenshot

![Screenshot](screenshot.png)

## Basic Configuration

The following are basic configuration options to get started quickly.

### Header

To define a custom header cover, set the property ``HEADER_COVER`` in ``pelicanconf.py``:

```python
HEADER_COVER = 'static/my_image.png'
```

Otherwise, you can define a simple header background color with the property ``HEADER_COLOR`` in ``pelicanconf.py``:

```python
HEADER_COLOR = 'black'
```

You can use any valid CSS color. Do note that this will be overridden by ``HEADER_COVER`` if defined, and also will be ignored by any Open Graph/Twitter card previews (falling back to a default image if ``HEADER_COVER`` or an article/page header is not defined.)

### Favicon

To use a favicon:

```python
FAVICON = 'favicon.ico'
```

**WARNING:** It is necessary to have ``STATIC_PATHS`` configured:

```python
STATIC_PATHS = ['images', 'extra/favicon.ico']
EXTRA_PATH_METADATA = {
    'extra/favicon.ico': {'path': 'favicon.ico'}
}
```

### Social URLs

Social URLs can be defined as a ``(name, url)`` tuple like so:

```python
SOCIAL = (('twitter', 'https://twitter.com/myprofile'),
          ('github', 'https://github.com/myprofile'),
          ('facebook','https://facebook.com/myprofile'),
          ('flickr','https://www.flickr.com/myprofile/'),
          ('envelope','mailto:my@mail.address'))
```

By default the links will show up as icons. For this to work correctly, the ``name`` needs to match the corresponding FontAwesome icon (case insensitive). If ``SHOW_SOCIAL_ON_INDEX_PAGE_HEADER`` is set to True, social icons will be shown under site sub-title on the index page. If you want text instead of icons, you can set ``NO_FONTAWESOME_FONTS`` to True (and then fix the capitalization of the names).

## Additional Article and Page Metadata

### Custom Headers

 - To customize the header cover image, insert the metadata ``header_cover``.
 - To customize Open Graph images, insert the metadata ``og_image``, otherwise ``header_cover``, ``HEADER_COVER``, or a default image is used.
 - To customize Twitter card images, insert the metadata ``twitter_image``, otherwise ``og_image``, ``header_cover``, ``HEADER_COVER``, or a default image is used.

All image paths are relative from the site root directory. You can also use absolute URLs for ``og_image`` and ``twitter_image``.

### Other Metadata

 - The metadata ``noindex`` can be set to ``True`` in order to have the article/page not be indexed by search engines

## Plugin Support

### Assets Support

If you have the ``pelican_webassets`` plugin enabled, all CSS will be put together in a large file. This will include your choice of code highlight, but it will NOT include your user defined CSS.

Assets requires that you have ``cssutils`` installed. This can be installed using ``pip``.

### Other Plugins Supported

These are some other Pelican plugins that are supported natively with this theme:

- ``better_code_samples``: Makes the code blocks with line numbers scrollable.
- ``readtime``: Adds "# minute read" to articles.
- ``share_post``: Adds old-school share URLs to the bottom of your articles (a non-tracking, non-JavaScript alternative to AddThis).

## Advanced Configuration

The following are advanced configuration options to tweak the theme to be just right.

### Header Height

By default the size of the header is large to display large images. If you'd like the header to be smaller, set the property ``HEADER_SMALLER`` in ``pelicanconf.py``:

```python
HEADER_SMALLER = True
```

### External Feed URL

You can specify an external feed URL (e.g. FeedBurner) in ``SOCIAL`` using the ``rss`` or ``rss-square`` icons (case insensitive). The icon (or text with ``NO_FONTAWESOME_FONTS`` set to True) will be shown in the footer with the rest of your ``SOCIAL`` accounts. A ``<link>`` tag for the external feed will be placed in ``<head>`` instead of the default Pelican feeds.

### Code Highlights

This theme contains these code color schemes:

 - Tomorrow - ``tomorrow.css``
 - Tomorrow Night - ``tomorrow_night.css``
 - Monokai - ``monokai.css``
 - Github - ``github.css``
 - Github Jekyll (Gray BG Jekyll way) - ``github_jekyll.css``
 - Darkly (Default) - ``darkly.css``

To customize, define ``COLOR_SCHEME_CSS`` in ``pelicanconf.py`` with the CSS filename. Example:

```python
COLOR_SCHEME_CSS = 'monokai.css'
```

### User Defined CSS

Define ``CSS_OVERRIDE`` in ``pelicanconf.py`` to insert a user defined CSS file after theme CSS. Example:

```python
CSS_OVERRIDE = 'myblog.css'
```

### Disable Custom Fonts

If you want to further slim down your site, you can disable Google and FontAwesome fonts.

For disabling Google fonts, you will notice that the page loads faster and uses less bandwidth, at the cost of using a font that is close to but not completely the same as the original Google font.

For disabling FontAwesome fonts, you will notice that your social icons change into text only links (as well as the page loading faster and using less bandwidth).

Simply set the following variables for disabling either of them:

```python
NO_GOOGLE_FONTS = True
NO_FONTAWESOME_FONTS = True
```

### User Defined Footer

Define ``FOOTER_INCLUDE`` in ``pelicanconf.py`` to insert a custom footer text instead the default "Powered by Pelican". The value is a template path. You also need to define the ``EXTRA_TEMPLATES_PATHS`` setting. If your custom footer template is stored under the content ``PATH`` then Pelican will try to render it as regular HTML page and will most likely fail. To prevent Pelican from trying to render your custom footer add it to ``IGNORE_FILES``. Example:

```python
FOOTER_INCLUDE = 'myfooter.html'
IGNORE_FILES = [FOOTER_INCLUDE]
EXTRA_TEMPLATES_PATHS = [os.path.dirname(__file__)]
```

**WARNING:** Avoid using names which duplicate existing templates from the theme directory, for example ``footer.html``. Due to how Pelican searches the template directories it will first find the files in the theme directory and you will not see the desired results.

### Analytics

Supported analytics include:

 - Google Analytics: ``GOOGLE_ANALYTICS``
 - Gauges: ``GAUGES``
 - Piwik: ``PIWIK_URL`` and ``PIWIK_SITE_ID``

### Other configuration

 - If ``ADDTHIS_PUBID`` is defined, sharing buttons from AddThis will appear at the bottom of articles
 - Google site verification token can be defined with ``GOOGLE_SITE_VERIFICATION``
 - Set ``SHOW_FULL_ARTICLE`` to True to show full article content on index.html
 - Set ``SHOW_ARTICLE_SUMMARY`` to True to show the article summary on index.html
 - Set ``SHOW_SITENAME_IN_TITLE`` to True to append your ``SITENAME`` to the end of all page titles (except index.html, since the page title is just your ``SITENAME``). This will be seen in the browsers tab name and in search results (whatever looks at the ``<title>`` tag).
 - Set ``SHOW_SITENAME_IN_OG_TITLE`` to True to append your ``SITENAME`` to the end of all titles (except index.html) that show up in Open Graph/Twitter cards (whatever looks at ``<meta property="og:title">`` tags). Not normally needed, as your domain name will still show up in the preview card, but might be useful if your domain name and blog name differ.
 - Set ``FACEBOOK_ADMINS`` to a list of Facebook account IDs which are associated with this blog. For example ``['12345']``. For more info see https://developers.facebook.com/docs/platforminsights/domains