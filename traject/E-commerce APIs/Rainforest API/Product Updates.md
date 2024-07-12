Product Updates
---------------

We're continuously updating VALUE SERP to add features and functionality, most of which are a direct result of requests from customers. See the latest updates below. Within the [VALUE SERP Dashboard](https://app.valueserp.com/product-updates) you can subscribe to be alerted via email when new updates are released.

| April 2024 |
| Update Type | Detail |
| --- | --- |
| New Feature | Google Search: Discussions and Forums added to VALUE SERP's search resultsGoogle’s Discussions and Forums are now included in VALUE SERP's search results. The Discussions and Forums object provides links to various forums and online discussions. For example, if you are searching "Planning a Disney vacation," Google will link you to discussions and forums to help you research the topic. The VALUE SERP discussions\_and\_forums object returns the properties: discussion\_title, link, source information and block\_position in its results.

Read More |
| March 2024 |
| Update Type | Detail |
| --- | --- |
| New Feature | Questions and Answers are now included in VALUE SERP's Google resultsGoogle’s Questions & Answers is a SERP feature that lists the sources for closely related questions and answers based on the question asked in a search query. VALUE SERP's questions\_and\_answers object returns the properties: question, answer, votes and source in its results.

Read More |
| New Feature | Google Search: Explore Brands results availableVALUE SERP now returns the explore\_brands object in Google search results (desktop and mobile). The Explore Brands object lists suggested brands based on the search query with product descriptions and links to the product. Properties included are: title, description, link, image and description.Note: This feature is currently only available for engine=google.

Read More |
| July 2023 |
| Update Type | Detail |
| --- | --- |
| | Meet Our Newest API! 🎉We’ve just launched Backyard API, our real-time Lowe’s product data API and companion to BigBox API for home improvement data. Let us know what you think of our newest addition or if you need any help. As always, you can try it out free! |
| June 2023 |
| Update Type | Detail |
| --- | --- |
| New Feature | Google Search: Shopping graph results availableVALUE SERP can now return the shopping elements that appear in Search results (desktop and mobile) as shopping\_graphs. This Google feature is currently available only for searches on google.com.

Read More |
| Enhancement | Ad\_carousel (sponsored) is now returned in Google Shopping search resultsAd\_carousel is an array of Sponsored Shopping Result objects found within the carousel.

Read More |
| April 2023 |
| Update Type | Detail |
| --- | --- |
| | Business UpdateAs a result of significant growth, our infrastructure — namely the dynamic routing of traffic to accommodate high volume customers — has recently required updates. Reworking architecture patterns and proxy configurations has taken us a fair amount of time, which in turn has led to some slower customer issue resolution.We'd like to assure you that we’ve identified and corrected the infrastructural shortcomings, and the outcome is a 50% increase in infrastructure and proxy capacity. We apologize for the potential business interruptions you may have experienced over the last couple months. Our aim is to earn your trust back and continue to support the realization of your business goals. Please don’t hesitate to get in touch if you require further information. |
| Feburary 2023 |
| Update Type | Detail |
| --- | --- |
| Enhancement | Geo-target by latitude and longitude for Google searchesVALUE SERP can now target Google searches by latitude and longitude. Location:lat:37.32646,lon:-121.80163 Make sure to include the gl & hl parameters. 

Read More |
| November 2022 |
| Update Type | Detail |
| --- | --- |
| Enhancement | Live and Video result types added for Google Top StoriesTwo new boolean properties video and live have been added to top\_stories results. True if a top story is video format, False if not. And True when a top story is a live video, False if not.

Read More |
| July 2022 |
| Update Type | Detail |
| --- | --- |
| Enhancement | Search Tabs added to organic SERP resultsA search\_tabs array property has been added to the search\_information object for organic SERP pages. This new property shows which search result types (i.e. Maps, Images, News etc) are available for the given query.

Read More |
| Enhancement | Scholarly Articles returned for organic web searchesA new field scholarly\_articles has been added to the APIs organic web search results to expose the Scholarly Articles section (containing links to Google Scholar) at the top of the SERP.

Read More |
| June 2022 |
| Update Type | Detail |
| --- | --- |
| New Feature | Support for custom S3-compatible object stores in DestinationsIt's now possible to specify a custom S3 endpoint to have Destinations upload Result Sets to any S3 compatible object store.

Read More |
| May 2022 |
| Update Type | Detail |
| --- | --- |
| Enhancement | Typical Prices from Across the Web parsed for Google ProductsA new property for Google Product parsing has been added - typical\_prices\_across\_web. The property shows the low and high price values, parsed with currency values.

Read More |
| April 2022 |
| Update Type | Detail |
| --- | --- |
| Enhancement | Enhanced Film Info parsingA new film\_info object has been added to the organic web search parsing to extract detailed information about film listings, including title, genre, reviews, VOD services etc.

Read More |
| Feburary 2022 |
| Update Type | Detail |
| --- | --- |
| New Feature | Inline Recipes returned in Google web results A new inline\_recipes property has been added to regular Google organic web search results to return the food recipe data shown inline with organic search results.

Read More |
| Enhancement | Enhanced "about this result" Google organic results parsingThe about\_this\_result parsing has been updated to extract the "search terms" and "related terms" sections of the result.

Read More |
| January 2022 |
| Update Type | Detail |
| --- | --- |
| New Feature | Nested Results added to organic results parsingA new nested\_results array, showing any results nested under an organic result, has been added to objects in the organic\_results array for regular web search results.

Read More |
| November 2021 |
| Update Type | Detail |
| --- | --- |
| Enhancement | Select all CSV FieldsWe have added Select All / Select None options to quickly select all CSV fields in the Batch editor and API Playground to make choosing CSV fields much quicker.

Read More |
| September 2021 |
| Update Type | Detail |
| --- | --- |
| Enhancement | "has\_product\_page" property added to Shopping resultsA new boolean proper has\_product\_page has been added to search\_type=shopping results. When has\_product\_page=true you may use the id property in a subsequent search\_type=product requests' product\_id field to request data from that individual product's landing page.Not all results on Google Shopping have an individual product landing page, so you can use the has\_product\_page property to determine whether a product page is available.

Read More |
| Enhancement | Video results - "date\_utc" and "domain" fields addedTwo news fields have been added to the Google Video results - domain and date\_utc (date UTC is an API-parsed ISO timestamp for the relative date time - i.e. "5 hours ago" shown next to the Google Video result).

Read More |
| New Feature | "Related Products" added to the Google Products API resultsRelated Products, as shown in the carousel on the Google Product landing page, have been added to the search\_type=product request. Price, rating, link, image and product title are retrieved.

Read More |
| Enhancement | Filter Batches by Last Run dateThe Batches List API has been updated to allow sorting Batches by last\_run date. You can also now filter the Batches by date using the last\_run\_before and last\_run\_after request parameters.The Batches Dashboard has also been updated to show the Last Run date for each Batch.

Read More |
| August 2021 |
| Update Type | Detail |
| --- | --- |
| Enhancement | Per-minute Batch scheduling improvementsThe Per X Minutes Batch scheduling options have been extended to allow you to run Batches on a "Per X Minute" schedule restricted to specific hours of the day and days of the week or month.The schedule\_hours, schedule\_days\_of\_week and schedule\_days\_of\_month can now be used with schedule\_type=minutes Batches for additional flexibility.This allows for scenarios such as "run this Batch every 5 minutes, between 9am and 5pm, on weekdays only".

Read More |
| New Feature | Run Batches on a per-minute scheduleBatches can now be scheduled on a per-minute basis, in addition to the existing hourly, daily, weekly and monthly schedules.Set schedule\_type=minutes when creating your Batch and specify the per-minute schedule using the schedule\_minutes parameter.Per-minute schedules of every minute up to every hour are supported.

Read More |
| New Feature | Grouped "related searches"VALUE SERP will now return expanded related searches (in addition to the standard related searches already returned) that are grouped under a particular group heading. New properties have been added to the related searches array showing the group name and type. Regular related searches will have type=standard and grouped related searches will have type=group. When type=group then the group\_name property is populated.

Read More |
| New Feature | Local Service Sponsored Ads parsing addedLocal Service Ads parsing has been added to the API's response and is exposed in the local\_service\_ads property.

Read More |
| Enhancement | Rich snippets attributes extractionParsing of the name/value pair attributes from the rich snippet section of organic results has been added to the API's parsing.

Read More |
| New Feature | New Batches API endpoint to Stop All queued and running BatchesThe new Stop All Batches API endpoint allows you to stop all running and queued Batches on your account in one API call. Useful if you have accidentally started a large number of Batches and need a quick way to set them all back to idle.

Read More |
| July 2021 |
| Update Type | Detail |
| --- | --- |
| New Feature | Android and iPhone browsers available for mobile SERP parsingThe new mobile\_type parameter allows you to choose to execute your device=mobile requests using an Android or iPhone mobile browser. |
| We started publishing Product Updates in June 2021, please refer to update emails for updates before this date. |
