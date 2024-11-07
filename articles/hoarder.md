# Hoarder - The Self-Hosted Bookmark Manager

Currently, I am using [wallabag](https://wallabag.org/) for read-it-later, [Anybox](https://anybox.app/) for bookmarking and quick retrival via Alfred, and [DEVONthink](https://www.devontechnologies.com/apps/devonthink) for archiving the booksmarks from wallabag and Anybox to better support full text searching (I wrote [a script](https://github.com/yinan-c/Anybox-sync-Devonthink/blob/main/anybox_to_devonthink.py) that checks the Anybox API for new links and save them to DEVONthink, which is modified from the [Anybox alfredworkflow](https://alfred.app/workflows/anybox/anybox/)).

This workflow has been robust and reliable for me, but I am always looking for better selfhosted tools to improve my workflow. There are two things currently missing:

1. Full text search is something Anybox doesn't have yet. While I write this article, May 2024, it is still under review in the [canny page of Anybox](https://anybox.canny.io/feature-requests/p/full-text-search).

2. Organizing bookmarks. I have a lot of bookmarks. I appreciate the Inbox ideology of Anybox, and the implementation of folders+tags+smart folders, but I still rely a lot on searching instead of mannually organizing (and again anybox is not providing full text search yet). It might help if there is an automatic organization feature like AI tagging or Smart Rules in DEVONthink.

So, trying out [Hoarder](https://github.com/hoarder-app/hoarder) app today. I would like to see whether it would compete Anybox as my main bookmark manager. Also I do like self-hosting services, and hoarding stuff 🤭.

At first sight, it feels like a complete app that I can directly put in production, it has a iOS app with share sheet support, chrome extension for easily save from browser, it saves note and images. And I really like the ability to have AI tagging for links and images so that I don't have to manually organize them. 

However, there are some features missing before it can become my main bookmark manager. 

- [REST API](https://github.com/hoarder-app/hoarder/issues/43) - for easily exporting data like links, tags, and for an Alfred workflow.
  > For now, it provides a CLI tool, but I am installing the app on my homeserver instead of my laptop. I will have to ssh to use the CLI, not ideal. A REST API would be good for remotely managing data.
- [Easy data export and backup](https://github.com/hoarder-app/hoarder/issues/75)
  >I don't seem to find a very good way to export data easily, for example screenshots, local cache, links.
- Offline archiving
  >For now, Hoarder supports plain text caching and screenshots. It would be good to see other formats supported (Planned, as of May 2024)
  update: As of Nov 2024, it supports full page archival (using [monolith](https://github.com/Y2Z/monolith)) to protect against link rot.
- [Local scrapper](https://github.com/hoarder-app/hoarder/issues/172) to fetch content after user login for some sites.
  >What I like about Anybox is its integration with [SingleFile extension](https://github.com/gildas-lormeau/SingleFile). It can directly save the .html downloaded to Anybox via API, so that any content behind paywall will also be downloaded. 
  >(It actually addresses the pity that SingleFile metadata only contains the first part of the full domain - it will only show something like https://github.com, when you directly download a  html with SingleFile metadata to DEVONthink)

Other features could be useful:
- RSS subscription link
  >Like what [linkding](https://github.com/sissbruecker/linkding) and [wallabag](https://wallabag.org/) provides. I am currently relying on RSS to sync my read-it-later from wallabag to DEVONthink and to my kindle with [kindleear](https://github.com/cdhigh/kindleear).

To conclude, I will not replace Anybox/wallabag with Hoarder for now. But it is a very young and promising open-source app with rapid iteration, someday it might will.