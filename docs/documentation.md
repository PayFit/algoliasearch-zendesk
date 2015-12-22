---
layout: page
title: Documentation
permalink: /documentation/
---


To be able to setup your new search on your Zendesk Help Center you'll need to have an Algolia account with a configured Zendesk Help Center crawler.

### Extracting your data to Algolia

This crawler feature is still in beta, just send us an email to be part of the program!

 * An Algolia account (our Hacker/FREE plan probably fits your need)
 * A Zendesk API token
 * The associated Zendesk application name & email

### Updating your Help Center theme

Once your data has been extracted to Algolia, you need to update your Help Center theme in order to replace the search feature by Algolia.

 * Click "Customize the design"
 * Select the "Document Head" template and add the following lines:

```html
<link rel="stylesheet" type="text/css" href="//cdn.jsdelivr/algoliasearch-zendesk/1/algoliasearch-zendesk.min.css">
<script type="text/javascript" src="//cdn.jsdelivr/algoliasearch-zendesk/1/algoliasearch-zendesk.min.js"></script>
<script type="text/javascript">
  algoliasearchZendeskHC({
    applicationId: '<YOUR APPLICATION_ID>',
    apiKey: '<YOUR SEARCH ONLY API KEY>',
    subdomain: '<YOUR ZENDESK APPLICATION NAME>',

    //
    // Optional configuration:
    //
    indexPrefix: 'zendesk_',    // or you custom <INDEX_PREFIX>
    baseUrl: '/hc/',            // the base URL of your Help Center
    colors: {
      primary: '#D4D4D4',       // the primary color
      secondary: '#D4D4D4'      // the secondary color
    },
    autocomplete: {
      enabled: true,            // is the autocomplete feature enabled?
      inputSelector: '#query',  // the DOM selector to select the search box
      sections: {
        enabled: true,          // does the autocomplete menu embed a 'sections' section
        hits: 3                 // the number of suggestions to display
      },
      articles: {
        enabled: true,          // does the autocomplete menu embed a 'articles' section
        hits: 3                 // the number of suggestions to display
      }
    },
    instantsearch: {
      enabled: true,
      tagsLimit: 15             // Maximum number of tags to display
    },
    translations: {             // These accept strings or objects associating locale with value
                                // e.g. {
                                //   found_in: {
                                //     'en-us': 'Found in',
                                //     'fr': 'En'
                                //   }
                                // }
      article: 'Article'
      articles: 'Articles'
      categories: 'Categories'
      sections: 'Sections'
      tags: 'Tags'
      search_by: 'Search by'
      no_result: 'No result'
      result: 'Result'
      results: 'Results'
      found_in: 'Found in'
      search_by: 'Search by'
      placeholder_autocomplete: 'Search in sections and articles'
      placeholder_instantsearch: 'Search in articles'
    }
  });
</script>
```