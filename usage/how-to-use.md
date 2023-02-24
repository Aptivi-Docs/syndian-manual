---
description: How do you use it?
---

# 🖥 How to use

Using this library is very simple! Just use the `Syndian.Instance` namespace in any piece of code you want to use the library, as in: `using Syndian.Instance;`

Just create a new instance of the `RSSFeed` class that contains the necessary constructor to allow you to get information about the feed.

```csharp
public RSSFeed(string FeedUrl, RSSFeedType FeedType)
```

where:

* `FeedUrl`: specifies the URL to the RSS feed, for example, [https://www.techrepublic.com/rssfeeds/articles/](https://www.techrepublic.com/rssfeeds/articles/)
* `FeedType`: specifies the feed type to parse
  * `RSS2`: Assumes that the RSS feed in the given URL is an RSS 2 feed
  * `RSS1`: Assumes that the RSS feed in the given URL is an RSS 1 feed
  * `Atom`: Assumes that the RSS feed in the given URL is an Atom feed
  * `Infer`: Automatically detects the RSS feed type

For the RSS feed info, `RSSFeed` contains the following properties:

* `FeedUrl`: URL to the feed
* `FeedType`: Feed type as described above
* `FeedTitle`: Feed title provided by the host
* `FeedDescription`: Feed description provided by the host
* `FeedArticles`: List of feed articles

FeedArticles is a list of feed articles, `RSSArticle`, that you can enumerate within the for loop, for example:

```csharp
var feed = new RSSFeed("feedurl", RSSFeedType.Infer);
foreach (RSSArticle article in feed.FeedArticles)
{

}
```

This class contains the following properties:

* `ArticleTitle`: Title of the article
* `ArticleLink`: Link to the article
* `ArticleDescription`: Description or summary of the article
* `ArticleVariables`: Additional article parameters
