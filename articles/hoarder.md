# Trying Out Hoarder - The Self-Hosted Bookmark Manager

Trying out [Hoarder](https://github.com/hoarder-app/hoarder) app today, to see whether it would competes Anybox as my main bookmark manager. I do like self-hosting services, and I like hoarding stuff 🤭.

At first sight, it feels like a complete app I can put in production, it has a iOS app with share sheet support, chrome extension for easily save from browser, it saves note and images.

I really like the ability to have AI tagging for links and images so that I don't have to manually organize them. And the full text search is something Anybox doesn't have yet. While I write this article, May 2024, it is still under review in the [canny page of Anybox](https://anybox.canny.io/feature-requests/p/full-text-search).

However, there are some features missing before it can become my main bookmark manager. 

- [REST API](https://github.com/hoarder-app/hoarder/issues/43) - for easily exporting data like links, tags, and for an Alfred workflow.
  > For now, it provides a CLI tool, but I am installing the app on my homeserver instead of my laptop. I will have to ssh to use the CLI, not ideal. A REST API would be good for remotely managing data.
- Easy data export
  >I don't seem to find a very good way to export data easily, for example screenshots, local cache, links.
- Offline archiving
  >For now, Hoarder supports plain text caching and screenshots. It would be good to see other formats supported (Planned, as of May 2024)
- [Local scrapper](https://github.com/hoarder-app/hoarder/issues/172) to fetch content after user login for some sites.
  >What I like about Anybox is its integration with [SingleFile extension](https://github.com/gildas-lormeau/SingleFile). It can directly save the .html downloaded to Anybox via API, so that any content behind paywall will also be downloaded. 
  >(It actually addresses the pity that SingleFile metadata only contains the first part of the full domain - it will only show something like https://github.com, when you directly download a  html with SingleFile metadata to DEVONthink)

Other features could be useful:
- RSS subscription link
  >Like what [linkding](https://github.com/sissbruecker/linkding) and [wallabag](https://wallabag.org/) provides. I am currently relying on RSS to sync my read-it-later from wallabag to DEVONthink.

To conclude, it will not replace Anybox with Hoarder for now. But it is a very young and promising open-source app with rapid iteration, someday it might will.