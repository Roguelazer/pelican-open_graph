============
 Open Graph
============

This plugin adds Open Graph Protocol tags to your articles.


Usage
=====

To output the tags generated by this plugin, simply add this code in
your base.html template:

.. code-block:: jinja2


  {% if article %}
  {% for tag in article.ogtags %}
  <meta property="{{tag[0]}}" content="{{tag[1]|striptags|e}}" />
  {% endfor %}
  {% endif %}

  {% if page  %}
  {% for tag in page.ogtags %}
  <meta property="{{tag[0]}}" content="{{tag[1]|striptags|e}}" />
  {% endfor %}
  {% endif %}

Metadata values are constructed from the SITENAME and SITEURL
settings, from the article title, from the article slug, from the
article category and from these standard metadata tags:

- ``date``
- ``modified``
- ``tags``

The plugin also reads these metadata tags:

- ``og_image``, an URL to an image that will represent your article;
- ``og_description``, a short description of your article. If not
  provided, the description will be set to ``summary``, which is often
  too long;
- ``og_locale``, the locale of your article (e.g. 'fr_CA'). If not provided,
  the locale will be set to your Pelican settings ``LOCALE``.

Additionally, the plugin reads article.related_posts to set ``og:see_also``.
