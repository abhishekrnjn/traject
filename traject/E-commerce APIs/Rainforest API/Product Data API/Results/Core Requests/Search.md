Search Results
--------------

When making a request with the `type` [parameter](/docs/product-data-api/parameters/search) set to `type=search` Rainforest API will return search results from the Amazon domain specified in the `amazon_domain` parameter.

Search results are retrieved from the [search results page](https://www.amazon.com/s?k=memory+cards&s=price-desc-rank) on Amazon.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/search.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Search Results PageAn example of the JSON object returned from a Search request is shown below:

{"request\_info":{...}"request\_metadata":{...}"request\_parameters":{...}"search\_results":[...]"related\_searches":[...]"pagination":{...}"refinements":{...}"shopping\_advisors":[...]"ad\_blocks":[...]}CopyRainforest API returns the following properties for Search requests:

| Property | Type | Description |
| search\_results | array | An array of Search Result objects, containing each of the product results shown on the Search Results page. The Search Result object has the following properties:positionnumberThe position of the result on the search results page.titlestringThe product name.brandstringThe product brand (where shown, note that not all search results page layouts break out the brand separately to the title).asinstringThe Amazon product ID (ASIN) for the product.linkstringThe product page link.is\_primebooleanDetermines whether the product is Prime-eligible or not.kindle\_unlimitedbooleanBoolean set to true when the "Kindle Unlimited" badge was shown next to the search result.prime\_videobooleanDetermines whether the product is a Amazon Prime Video product, or not.is\_amazon\_brandbooleanSet to true when the "Amazon Brand" banner is shown next to the search result.is\_exclusive\_to\_amazonbooleanSet to true when the "Exclusive to Amazon" banner is shown next to the search result.is\_small\_businessbooleanSet to true when the "Small Business" banner is shown next to the search result.is\_amazon\_freshbooleanDetermines whether the product is an Amazon Fresh product, or not.is\_whole\_foods\_marketbooleanDetermines whether the product is a Whole Foods Market product, or not.couponobject| Coupon Object | Present when the "Coupon" badge is shown next to the search result. Contains the following properties: |
| --- | --- |
badge\_textstringThe text shown inside the coupon badge (i.e. "Save 5%").textstringThe text shown next to the coupon badge (i.e. "with coupon").dealobject| Deal Object | Present when the "Deal" badge is shown next to the search result. Contains the following properties: |
| --- | --- |
linkstringA link to the deal landing page.textstringThe text shown next to the deal badge (i.e. "Limited time deal").badge\_textstringThe text shown inside the deal badge (i.e. "16% off").climate\_pledge\_friendlyobject| Climate Pledge Friendly Object | Present when the "Climate Pledge Friendly" badge is shown next to the search result. Contains the following properties: |
| --- | --- |
linkstringA link to the product landing page showing more detail on the Climate Pledge Friendly messaging.textstringThe text of the Climate Pledge Friendly certification.imagestringAn image URL to the logo of the Climate Pledge Friendly certification logo, if shown.gift\_guideobject| Gift Guide Object | Present when the "Gift Guide" badge is shown next to the search result. Contains the following properties: |
| --- | --- |
linkstringA link to the deal landing page.badge\_textstringThe text shown inside the gift guide badge (i.e. "Holiday gift guide"). Can be useful in determining the "type" of gift guide the search result appears in.amazons\_choiceobject| Amazons Choice Object | Present when the "Amazon's Choice" badge is shown next to the search result. Contains the following properties: |
| --- | --- |
linkstringA link to the product.keywordsstringThe keywords for which this search result is "Amazon's Choice".bestsellerobject| BestSeller Object | Present when the "BestSeller" badge is shown next to the search result. More detailed bestseller information can be retrieved from the product page by making a type=product request specifying this search results ASIN. Contains the following properties: |
| --- | --- |
linkstringA link to the Bestsellers page to which this bestseller badge relates.categorystringThe category name for which this product is a best seller, i.e. "USB Cables".imagestringA link to the image of the product.sponsoredbooleanSet to true or false depending on whether the search result is a sponsored listing, or not.featured\_from\_our\_brandsbooleanSet to true when the product is flagged as "Featured from our Brands", omitted otherwise.authorsarray| Authors Array | The authors property contains the authors or artists of the product. Mainly applies to books, music and video products. The author object has the following properties: |
| --- | --- |
namestringThe name of the author or artist.linkstringThe link to the author or artist on the Amazon domain, if present.narrated\_byarray| Narrated-By Array | The narrated-by property contains the narrators of the product. Only applies for Audible Amazon Domains. The narrated-by object has the following properties: |
| --- | --- |
namestringThe name of the narrator.linkstringThe link to the narrator on the Audible Amazon domain, if present.runtimeobject| Runtime Object | The runtime object contains runtime of the podcast. Only applies for Audible Amazon Domains. The runtime object has the following properties: |
| --- | --- |
rawstringThe raw runtime as shown on the Audible domain.add\_on\_itemobject| Add-On Item Object | The add-on item object is present when the item is part of the Amazon 'add-on item' program. The property will be omitted if the product is not an add-on item. |
| --- | --- |
is\_add\_on\_itembooleanTrue/false indicating whether the product is an add-on item.availabilityobject| Availability Object | The Availability object is present when Amazon show availability (i.e. stock level) data next to the search reult. The availability property will be omitted if availability information is not shown alongside the search result. The availability object contains the following properties: |
| --- | --- |
rawstringThe raw availability as shown next to the search result, for example "Only 1 left in stock - order soon".categoriesarray| Categories Array | An array containing details of the categories shown with this product as displayed next to the search bar at the top of the page. Each object in the array contains the following properties: |
| --- | --- |
namestringThe name of the category (i.e. "Toys & Games").ratingnumberThe overall rating of the product, out of 5.ratings\_totalnumberThe total number of customer ratings the product has received.deliveryobject| Delivery Object | The Delivery object is present when Amazon show delivery information neat to the search result. The delivery object contains the following properties: |
| --- | --- |
taglinestringA string containing the tagline associated with the delivery option, for example "Get it as soon as Sat, Oct 3".priceobjectA price object representing the price and currency of the delivery option. The delivery price object has the same properties as the price objects in the prices arrayis\_carouselbooleanSet to true when this search result is part of a carousel. It is not present if the search result is not part of a carousel. If is\_carousel=true then the carousel property describes the properties of the carousel this search result if part of.carouselobject| Carousel Object | When a search result is part of a "carousel" (a horizontally scrolling row of search results nested within the main search results) then the carousel object is present. The carousel object contains details of the carousel that this search result is part of. Examples of carousels could be "Highly Rated" or "Today's Deals". The carousel object contains the following properties: |
| --- | --- |
titlestringThe title of the carousel that this search result is part of, for example "Highly Rated".sub\_titlestringThe subtitle of the carousel that this search result is part of, for example "Based on star rating and number of customer ratings".sponsoredbooleanSet to true when the carousel itself (as-shown in the carousel header section) indicates that the contents of the carousel are all sponsored results.idbooleanThe ID of the carousel that this search result is part of.total\_itemsbooleanThe total number of items in the carousel that this search result is part of.pricesarray| Prices Array | The prices array contains details about the products pricing, as shown underneath the product title. It is an array of price objects, the properties of which are described below: |
| --- | --- |
symbolstringThe currency symbol, i.e. $ for USD.valuenumberThe price of the Offer.currencystringThe currency of the Offer as a ISO 4217 currency code.rawstringThe raw price as displayed on the Offer listing.namestringThe name of the price if applicable, for example "Kindle", "Hardcover".priceobjectA price object representing the first item in the prices array. This is normally the "main" price for the product and is included as a convienience to make extracting the main price easier.informationstringThe information text, typically shown in bold below the product title and showing the pack quantity. For example 25.4 Fl Oz (Pack of 2).unit\_pricestringThe product unit price, where shown. For example $0.57/Fl Oz.other\_formatsstringAn array of objects containing asin, link and title properties showing the 'other format' links shown next to the search result. Typically found on books or music categories. .recent\_salesstringThe product recent sales, where shown. For example 200+ bought in past week.recent\_viewsstringThe product recent views, where shown. For example 300+ viewed in past week. |
| search\_information | object | An object containing details of the current page of search results.spelling\_correctionstringPopulated with the spelling correction shown when a misspelled search\_term is provided.Note you can control whether the spelling correction is automatically followed by using the direct\_search=true request parameter.original\_search\_termstringPopulated with the spelling correction shown when a misspelled search\_term is provided.did\_you\_meanstringPopulated with the "did you mean" spelling correction shown when a misspelled search\_term is provided and the direct\_search=true request parameter is set.no\_results\_foundbooleanSet to true when the "no results found, showing results from all departments" banner is shown at the top of the search result page. |
| related\_searches | array | An array of "related\_search" objects detailing the related searches shown at the bottom of the search results page.linkstringThe link to the related search results.querystringThe query text of the related search. Could be used in a future type=search request to retrieve the related search results. |
| related\_brands | array | An array of "related\_brand" objects detailing the sponsored related brands shown at the bottom of the search results page.logostringA link to the brand logo image of the related brand, if shown.imagestringA link to the product image shown in the related brand, if shown.titlestringThe title text of the related brand.linkstringThe link shown in the related brand section.store\_namestringThe name of the store of the related brand (if shown).store\_idstringThe ID of the store of the related brand (if shown). Can be used in the store\_id parameter of subsequent a Store request to retrieve listings from the store.store\_linkstringA link to the store of the related brand (if shown). |
| pagination | object | An object containing details of the current search results page and the total number of pages that are available. To paginate you should specify the page number in your request's page parameter.total\_resultsnumberThe total number of results Amazon show in the header bar. Note that it will not normally be possible to paginate through to very high page numbers however total\_results is useful as an indication of market size.current\_pagenumberThe current page number.total\_pagesnumberThe total number of pages available. |
| refinements | object | An object containing details of the available refinements for the given search results. These allow you to refine your search by values such as "Reviews rating 4 and over", "price range" and "brand". To refine your search results by a given refinement value you should specify refinement values, comma seperated, in your request's refinements parameter.Refinement values are dynamic and change by category area or search term used. If you wish to use refinements you should first issue a type=search request without specifying any refinements to retrieve a master list of the avaialble refinements for the given category area/search term. You can then cache these refinement values for use on subsequent requests.The refinements object has a property name for each refinement that is available. This property contains an array showing the full-text refinement name and an value. It is this value that you should specify, comma seperated, in your request's refinements parameter.namestringThe full-text name of the refinement, for example "Brand".valuestringThe value of the refinement, you should specify the refinement value(s), comma seperated, in your request's refinements parameter.linkstringThe link shown for the refinement, you can use the link in a new type=search request's url parameter to navigate to the search results filtered by this refinement. |
| shopping\_advisors | array | An array of "shopping advisor" objects detailing the shopping advisor sections shown inline in the search results page. These can have headings such as "Editorial recommendations" or "Highly rated and well-priced products". The typically contain editorial content along with a selection of recommended products.positionnumberThe position of the shopping advisor within the search results. For example, position=5 indicates the shopping advisor was shown after the product at position=4 in the search\_results array.titlenumberThe title of the shopping advisor section.profileobject| Profile Object | The profile object contains details about the person or organisation who is the author or content-provider for the Shopping Advisor's Amazon profile: |
| --- | --- |
namestringThe profile name of the author.linkstringA link to the Amazon profile for the author.idstringThe Amazon profile ID of the author or content-provider.articleobject| Article Object | The article object is present when the author of content-provider has provided editorial or article content to accompany the Shopping Advisor section. |
| --- | --- |
titlestringThe title of the article.bodystringThe body text of the article.linkstringA link to the article.datestringA text representation of the publication date of the article.totalnumberThe total number of product recommendations shown in this Shopping Advisor.recommendationsobject| Recommendations Array | The recommendations array contains a list of recommended products shown in the Shopping Advisor. |
| --- | --- |
positionnumberThe position of the recommended product in the Shopping Advisor.titlestringThe title as-provided by the author or content-provider as to why this product is recommended, i.e. "Good Value".sub\_titlestringThe subtitle of the recommendation, i.e. "Durable Design".bodystringThe body text of the recommendation.productobjectAn object representing the recommended product. It has the same properties as objects in the main search\_results array (i.e. title, asin, link, image, price, is\_prime, rating and ratings\_total |
| ad\_blocks | array | An array of "ad block" objects detailing the sponsored ad blocks shown above or inline on the search results page. Typically ad blocks contain detail about the creative (the ad launch date, title) along with a link to the target Ad page and a selection of ASIN details.creative\_idstringThe ID of the creative shown in the Ad Block.campaign\_idstringThe ID of the campaign the ads in the Ad Block belong to (if shown).advertiser\_idstringThe advertiser ID of the advertiser the video block belongs to (if shown).ad\_idstringThe ID of the Ad Block.brand\_logostringA link to the brand logo image of the Ad Block, if shown.background\_imagestringA link to the background image of the Ad Block, if shown.creative\_typestringThe name of the type of creative used in the Ad Block.linknumberThe link the user is redirected to when clicking the Ad Block.titlenumberThe title of the Ad Block, if shown.sub\_titlenumberThe subtitle of the Ad Block, if shown.store\_namestringThe name of the store of the advertiser the Ad Block belongs to (if shown).store\_idstringThe ID of the store of the advertiser the Ad Block belongs to (if shown). Can be used in the store\_id parameter of subsequent a Store request to retrieve listings from the store.store\_linkstringA link to the store of the advertiser the Ad Block belongs to (if shown).dateobject| Date Object | The date object contains details about the date the Ad Block was launched (if shown). It contains the following properties |
| --- | --- |
rawnumberThe raw date, expressed as an Unix EPOCH.utcstringThe date, parsed from the raw date, in ISO 8601 format. If Rainforest API cannot parse the raw date then this property will be null.productsarray| Products Array | The products array contains an array of objects containing details of products shown in the Ad Block: |
| --- | --- |
asinstringThe ASIN of the product shown in the Ad Block.linkstringThe product page link of the product shown in the Ad Block.imagestringA link to the image for the product shown in the Ad Block.titlestringA title of the product shown in the Ad Block.priceobjectA price object describing the price of the product shown in the Ad Block, if shown.is\_primebooleanSet to true if the Amazon Prime indicator is shown next to the product in the Ad Block.ratingnumberThe rating of the product shown in the Ad Block, out of 5.rating\_totalnumberThe total number of ratings the product shown in the Ad Block has received. |
| video\_blocks | array | An array of "video block" objects detailing the full-row sponsored video sections shown on the search results page. Typically video blocks contain a video, along with a link to one or more products related to the video.video\_linkstringA link to the video (typically a MP4 file) that plays in the video block.thumbnail\_linkstringA link to the thumbnail image that is shown before the video starts playing (typically while the video is buffering).campaign\_idstringThe campaign ID the video block belongs to.advertiser\_idstringThe advertiser ID of the advertiser the video block belongs to.has\_audiobooleanSet to true if the video includes audio.store\_namestringThe name of the store of the advertiser the video block belongs to (if shown).store\_idstringThe ID of the store of the advertiser the video block belongs to (if shown). Can be used in the store\_id parameter of subsequent a Store request to retrieve listings from the store.store\_linkstringA link to the store of the advertiser the video block belongs to (if shown).productsarray| Products Array | The products array contains an array of objects containing details of products shown in the Video Block: |
| --- | --- |
asinstringThe ASIN of the product shown in the Video Block.linkstringThe product page link of the product shown in the Video Block.is\_primebooleanSet to true if the Amazon Prime indicator is shown next to the product in the Video Block.imagestringA link to the image for the product shown in the Video Block.titlestringA title of the product shown in the Video Block.ratingnumberThe rating of the product shown in the Video Block, out of 5.rating\_totalnumberThe total number of ratings the product shown in the Video Block has received.priceobjectA price object describing the price of the product shown in the Video Block, if shown. |
Next Steps

* [Search Parameters](/docs/product-data-api/parameters/search)