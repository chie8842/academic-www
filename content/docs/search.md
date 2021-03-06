+++
title = "Search"

date = 2018-07-23
# lastmod = 2018-08-01

toc = true  # Show table of contents? true/false
type = "docs"  # Do not modify.

[menu.docs]
  parent = "setup"
  weight = 50
+++

A search box can be added to your site to empower your users to search your website content for keywords. If search is enabled, a search box can be shown on the home page (using the search widget) and in the sidebar of any content using the docs/tutorials layout (as can be seen on this site).

The search feature may either be powered by the **built-in** algorithm (based on *Fuse.js*) or powered by [Algolia](https://www.algolia.com). Alternatively, you can create your own third party (e.g. Google) search widget by following the guide in the [Alternatives](#alternatives) section below.

## Enable

To enable the search widget:

1. Academic **v2.4+** is required. [Update]({{< relref "/docs/update.md" >}}) if necessary.
1. Under `[params.search]` in `config.toml` choose your search provider
1. If `home/search.md` does not exist, copy the file from `themes/academic/exampleSite/home/search.md`
1. In `home/search.md` set `active` to true in order to activate the search widget

Continue reading below to learn how to configure your desired search provider.

### Built-in

To use the free integrated search engine:

1. Under `[params.search]` in `config.toml` set `engine = 1`

Note that this search engine runs entirely in the web browser on the visitor's device. Thus, it is not scalable to a very large number of pages. If you have a very large amount of content, we recommend opting for a server side search engine such as Algolia or Google (see below).

### Algolia

1. Under `[params.search]` in `config.toml` set `engine = 2`
1. Register a **free** [Algolia](https://www.algolia.com) account and follow their wizard to create a new search app 
1. Build your site by running the `hugo` command in Terminal or Command Prompt
1. Upload the generated `public/index.json` file to the *Indicies* page in your Algolia dashboard
1. Paste the Algolia *App ID*, *API Key*, and *Index Name* from the *Indicies* and *API Keys* pages of your Algolia Dashboard into the `[params.search.algolia]` section in `config.toml`
1. Under `[params.search]` in `config.toml`, set `engine = 1` to activate the Algolia search engine
1. Serve (or build and upload) your site and test out the shiny new search widget on your home page :smile:

Note that whenever your content changes (e.g. you add a new page), you will need to re-build and re-upload the search index to Algolia.

## Disable

1. Under `[params.search]` in `config.toml` set `engine = 0`
1. Delete `home/search.md` or set `active = false` in its front matter


## Alternatives

Alternative search providers, such as Google search, are not integrated into the *search* widget, but can be implemented by creating your own custom widget. For example,

1. Create a [custom widget]({{< relref "/widgets.md" >}}) in your `/content/home/` folder
1. Signup for [Google Custom Search Engine](https://cse.google.com/cse/)
1. Paste the HTML which Google provide into the body of your custom widget
