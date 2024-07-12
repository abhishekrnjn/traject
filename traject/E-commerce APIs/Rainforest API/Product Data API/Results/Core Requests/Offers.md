Offers Results
--------------

When making a request with the `type` [parameter](/docs/product-data-api/parameters/offers) set to `type=offers` Rainforest API will return all Seller Offers for the product specified in either the `asin` and `amazon_domain` parameters or the `url` parameter.

Offers are retrieved from the offers listing popup window for a single product on Amazon.

Note that the buybox-winner offer is always pinned to the top of the offers listing popup window, above the 'other offers'. Rainforest will append the buybox winner offer to the top of the `offers` array when `page=1`.

  
:::hint



**Stock Estimation**  
To get stock estimation for a specific Offer pass that offers `offer_id` into a [stock-estimation](/docs/product-data-api/parameters/stock-estimation) request.  
:::

![]()Amazon Offers Listing PageAn example of the JSON object returned from an Offers request is shown below:

{"request\_info":{...}"request\_metadata":{...}"request\_parameters":{...}"product":{...}"offers":[...]"pagination":{...}"available\_filters":{...}}CopyRainforest API returns the following properties for Offers requests:

  
:::hint



**Paginating Offers Results**  
Amazon returns 10 offers per page. To request more offers issue additional requests incrementing the `page` [parameter](/docs/product-data-api/parameters/offers). The `position` property shows the position of the offer within the current page of results. For example, the first offer of `page=2` would have `position=1`.  
:::

| Property | Type | Description |
| offers | array | An array of Offer objects, containing each of the Seller Offers shown on the Offers listing page. The Offer object has the following properties:positionnumberThe position of the offer within the current page of offer results.is\_primebooleanDetermines whether the Offer is Prime-eligible or not.offer\_idstringThe ID of the Offer. To get stock estimation for a specific Offer pass the offer\_id into a stock-estimation request.offer\_asinstringThe ASIN the offer relates to. Normally the same as the ASIN supplied in the asin parameter unless the request specifies show\_different\_asins=true.price\_only\_available\_in\_cartstringTrue / false depending on whether the price for this Offer is only available in the Cart. If no price is shown then the price may only be visible once the ASIN is added to the cart. You could consider a stock-estimation request to retrieve the price when price\_only\_available\_in\_cart=true.| Price Object | The price object contains details about the sellers pricing. |
| --- | --- |
symbolstringThe currency symbol, i.e. $ for USD.valuenumberThe price of the Offer.currencystringThe currency of the Offer as a ISO 4217 currency code.| Minimum Order Quantity Object | The minimum order quantity object contains details about the sellers minimum order quantity. |
| --- | --- |
valuenumberThe minimum order quantity of the Offer.| Maximum Order Quantity Object | The maximum order quantity object contains details about the sellers maximum order quantity. |
| --- | --- |
valuenumberThe maximum order quantity of the Offer.| Promotion Object | The promotion object contains details about any promotion associated with the seller offer. |
| --- | --- |
rawstringThe raw text of the promotion.| Import Fee Object | The Import Fee object contains details about any import fee payable on the offer. |
| --- | --- |
symbolstringThe currency symbol, i.e. $ for USD.valuenumberThe amount of the import fee.currencystringThe currency of the import fee as a ISO 4217 currency code.rawstringThe raw price as displayed on the import fee.| Condition Object | The condition object contains details about the products condition. |
| --- | --- |
is\_newbooleanUsed to quickly determine whether the product being offered is new or used.titlestringThe main description of the product condition, i.e. "Used - Very Good".commentsstringAny further comments about the product being offered, i.e. "Item will come repackaged."| Delivery Object | The deliery object contains details about the products delivery options. |
| --- | --- |
is\_freebooleanUsed to quickly determine whether free delivery is offered.fulfilled\_by\_amazonbooleanWhether the delivery is via Amazon, or a third party seller.shipped\_from\_outside\_countrybooleanWhether the product is shipped from outside the home country for the given Amazon domain (e.g. if an item on Amazon.ca is shipped from the United States).countdownstringThe countdown as displayed next to the offer, i.e. "20 hrs and 33 mins".commentsstringAny delivery comments, i.e. "On back order - expected 30th June".rawstringThe raw price as displayed for the delivery price (if present).priceobject| Delivery Price Object | The delivery price object contains details about the delivery pricing for the Offer. |
| --- | --- |
symbolstringThe currency symbol, i.e. $ for USD.valuenumberThe price for delivery.currencystringThe currency as a ISO 4217 currency code.upsellobject| Delivery Upsell Object | The delivery upsell object contains details about the upsell messages (if shown) for the offer. |
| --- | --- |
namestringThe name of the upsell message, for example "Fastest delivery".valuestringThe value of the upsell message, for example "Tomorrow" in the case of a "Fastest delivery" upsell message.undeliverablebooleanPresent, and set to true, when the offer is not deliverable to the current customer\_location. Absent if the product is deliverable.undeliverable\_messagestringWhen undeliverable=true, undeliverable\_message contains the message shown indicating why the offer is undeliverable.| Seller Object | The seller object contains details about the seller providing the Offer. |
| --- | --- |
namestringThe name of the seller.idstringThe ID of the seller. Can be specified as a request parameter to a type=seller\_profile request to view this sellers profile page.linkstringA link to the sellers shopfront on Amazon (for third party sellers).ratingnumberThe third party sellers rating, out of 5.ratings\_totalnumberThe total number of ratings that the third party seller has received in the last 12 months.ratings\_total\_percentagenumberThe % of all ratings received by the third party seller in the last 12 months that Amazon determines where "positive". |
| product | object | An object containing details of the product (in so far as those details are shown on the Offers listing page). For full product details you should issue a request with type=product to retrieve details from the product page.titlestringThe product name.categoriesarray| Categories Array | An array containing details of the categories shown with this product as displayed next to the search bar at the top of the page. Note that Amazon products can exist in multiple categories. Each object in the array contains the following properties: |
| --- | --- |
namestringThe name of the category (i.e. "Toys & Games").ratingnumberThe customer rating of the product, out of 5.reviews\_totalnumberThe total number of customer reviews the product has. To retrieve the reviews you should issue a request with type=reviews to retrieve details from the reviews pageimagestringA link to the image of the product.asinstringThe Amazon product ID (ASIN) for the product.sub\_titleobject| Subtitle Object | The subtitle object contains details of the information shown in the subtitle directly underneath the product title. |
| --- | --- |
textstringThe text of the subtitle - typically the brand name of the product i.e. "Samsung".attributesarray| Attributes Array | The attributes array contains details of the product attributes as shown underneath the product title. |
| --- | --- |
namestringThe name of the product attribute i.e. "Capacity".valuestringThe value of the product attribute i.e. "128 GB". |
| pagination | object | An object containing details of the current Offers page and the total number of Offers pages that are available. To paginate you should specify the page number in your request's page parameter.current\_pagenumberThe current page number.total\_pagesnumberThe total number of pages available. |
| available\_filters | object | An object containing details of which offer filters are shown by Amazon. Can be used to inform future type=offers requests.offers\_free\_shippingbooleanTrue/false depending on whether a offers\_free\_shipping filter is available.offers\_primebooleanTrue/false depending on whether a offers\_prime filter is available.offers\_condition\_newbooleanTrue/false depending on whether a offers\_condition\_new filter is available.offers\_condition\_used\_like\_newbooleanTrue/false depending on whether a offers\_condition\_used\_like\_new filter is available.offers\_condition\_used\_very\_goodbooleanTrue/false depending on whether a offers\_condition\_used\_very\_good filter is available.offers\_condition\_used\_goodbooleanTrue/false depending on whether a offers\_condition\_used\_good filter is available.offers\_condition\_used\_acceptablebooleanTrue/false depending on whether a offers\_condition\_used\_acceptable filter is available. |
Next Steps

* [Offers Parameters](/docs/product-data-api/parameters/offers)
