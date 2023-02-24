---
description: How does it work?
---

# ⚒ How it works

When you call the constructor of the `RSSFeed` or when you try to manually refresh the already-existing instance using either one of the following functions:

* `Refresh()`: refreshes the RSS feed using the current feed type and the current feed URL
* `Refresh(string, RSSFeedType)`: refreshes the RSS feed using the specified feed type and the specified feed URL

...Syndian attempts to fetch the feed content from the URL. After this happens, the XML document loader loads the content from the stream containing the XML response for the RSS feed information.

Before parsing starts, Syndian verifies the feed type by checking to see if the relevant tags exist for each RSS version:

* For RSS 2 feeds, `rss` element is checked.
* For RSS 1 feeds, `rdf:RDF` element is checked.
* For Atom feeds, `feed` element is checked.

If verification succeeds, Syndian will attempt to read both the title and the description from the feed info before going deep into the articles. Syndian will look for the following nodes:

* For RSS 2 feeds, `item` node in `<channel>` and `<item>` instances are checked
* For RSS 1 feeds, `item` node in `<channel>` or `<item>` instance is checked.
* For Atom feeds, `entry` node in `<feed>` instance is checked.

Syndian then goes on to make a new instance of the `RSSArticle` class with the following necessary information:

* Article title: `title` node
* Article link: `link` node
* Article summary: `summary`, `content`, or `description` node

It also checks to see if the embedded summary or description is in the HTML format or the text format. If the article is in the HTML format, it will try to extract the text from the HTML code found within the article description.

If applicable, it also fetches all the article parameters. Syndian then returns a new instance of the `RSSArticle` class with the above information installed.

Finally, the new `RSSFeed` class instance with the information about the feed is returned.
