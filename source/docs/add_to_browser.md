# Add HubGrep to your browser as a search engine 


## Firefox

Go to [hubgrep.io](https://hubgrep.io), and right click in the search field.
In the menu that pops up, click "Add a Keyword for this Search..."

```{image} ../_static/hubgrep_default_firefox0.png
:alt: a right click in the search field opens a menu containing "Add a Keyword for this search"
:class: bg-primary
:width: 500px
:align: center
```

This opens a window to to add this as a bookmark. The keyword triggers your search later.

```{image} ../_static/hubgrep_default_firefox1.png
:alt: in the "New Bookmark" window, add the keyword you want to use
:class: bg-primary
:width: 500px
:align: center
```

Afterwards, you can search by typing the keyword, followed by the query, in the addressbar!

```{image} ../_static/hubgrep_default_firefox2.png
:alt: afterwards search by prefixing the search string in the addressbar with the Keyword
:class: bg-primary
:width: 500px
:align: center
```

This works with all kinds of text inputs, not just HubGrep! :)

## Chromium

Open the settings and go to "Search engine" in the menu on the left.

In that category, click "Manage search engines".
Click the "Add" button to add a new search engine.

The URL should looke like `https://hubgrep.io/?s=%s`.


```{image} ../_static/hubgrep_default_chromium0.png
:alt: afterwards search by prefixing the search string in the addressbar with the Keyword
:class: bg-primary
:width: 500px
:align: center
```

Afterwards, same as Firefox: search by typing the keyword followed by the query in the address bar.

```{image} ../_static/hubgrep_default_chromium1.png
:alt: afterwards search by prefixing the search string in the addressbar with the Keyword
:class: bg-primary
:width: 500px
:align: center
```

## Qutebrowser


In [qutebrowser](), you can add search engines by adding them to `c.url.searchengines` in your config.

Edit `.config/qutebrowser/config.py`, and append HubGrep like this:

```python
c.url.searchengines = {
    'DEFAULT': 'https://duckduckgo.com/?kae=t&kad=de_DE&kp=-2&kn=1&q={}',
    'ddg': 'https://duckduckgo.com/?kae=t&kad=de_DE&kp=-2&kn=1&q={}',
    'wiki': 'http://de.wikipedia.org/w/index.php?search={}&title=Special:Search',
    'mediathek': 'https://mediathekviewweb.de/#query={}&everywhere=true',
    'deepl': 'https://www.deepl.com/en/translator#en/de/{}',
    'osm': 'https://www.openstreetmap.org/search?query={}',
    # ...
    'hubgrep': 'https://hubgrep.io/?s={}'
}
```

After restarting qutebrowser, you will get the search autocompletion in the `:open` dialog! (The one thats also triggered with `O`!) 


```{image} ../_static/hubgrep_default_qutebrowser.png
:alt: afterwards search by prefixing the search string in the addressbar with the Keyword
:class: bg-primary
:width: 500px
:align: center
```



