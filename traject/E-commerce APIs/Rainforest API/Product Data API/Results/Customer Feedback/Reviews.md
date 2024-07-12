Reviews Results
---------------

When making a request with the `type` [parameter](/docs/product-data-api/parameters/reviews) set to `type=reviews` Rainforest API will return all Customer Reviews for the product specified in either the `asin` and `amazon_domain` parameters or the `url` parameter.

Reviews are retrieved from the [customer reviews page](https://www.amazon.com/product-reviews/B073JYC4XM) for a single product on Amazon.

![]()Customer Reviews PageAn example of the JSON object returned from a Reviews request is shown below:

{"request\_info":{...}"request\_metadata":{...}"request\_parameters":{...}"product":{...}"summary":{...}"top\_positive":{...}"top\_critical":{...}"reviews":[...]"pagination":{...}}CopyRainforest API returns the following properties for Reviews requests:

  
:::hint



**Paginating Results**  
Amazon returns 10 reviews per page. To request more reviews issue additional requests incrementing the `page` [parameter](/docs/product-data-api/parameters/reviews).  
:::

| Property | Type | Description |
| reviews | array | An array of Review objects, containing each of the Customer Reviews shown on the Customer Reviews page. The Review object has the following properties:idstringThe unique, Amazon-assigned, ID of the customer review. This can be used by your app to flag whether you have previously processed this review on a prior request.titlestringThe title of the review.bodystringThe body text of the review.Note it's possible for a review to contain only a title, and no body. In this case the body property will be absent.body\_htmlstringThe HTML of the review body, useful if you wish to preserve HTML formatting.imagesarrayAn array of customer image objects containing a link property to the customer-supplied review image.videosarrayAn array of customer video objects containing a image property (linking to the video thumbnail image) and a video property (a link to the customer video file).linkstringThe link to the review. Note that in the case of Global Reviews (identified by having a review\_country other than that of the target Amazon domain and is\_global\_review=true) no link is published.ratingnumberThe product rating given by the reviewer, out of 5.helpful\_votesnumberThe number of helpful votes this review has received from other Amazon customers.commentsnumberThe number of comments this review has received.review\_countrystringThe country the review was written in (in the case of Amazon Global Reviews). Expressed as a two-letter ISO country-code.is\_global\_reviewbooleanTrue/false depending on whether this review is a Global Review (i.e. a review from another Amazon domain), or not. Note that Global Reviews do not have a link property. The home country of the Global Review can be found in the review\_country property.verified\_purchasebooleanWhether this reviewer is an Amazon-verified purchaser of the product.vine\_programbooleanWhether this reviewer reviewed this product under the Amazon Vine program.vine\_program\_free\_productbooleanWhether the Amazon Vine program "Vine Customer Review of Free Product" badge is shown. Only populated when vine\_program=true.attributesarray| Attributes Array | The attributes array contains details of the product attributes as shown underneath the product title on the customer reviews page. |
| --- | --- |
namestringThe name of the product attribute i.e. "Capacity".valuestringThe value of the product attribute i.e. "128 GB".| Date Object | The date object contains details about the date of the review. |
| --- | --- |
rawstringThe raw date as retrieved from the Amazon page.utcstringThe date of the review, parsed from the raw date, in ISO 8601 format. If Rainforest API cannot parse the raw date then this property will be null.| Profile Object | The profile object contains details of the profile of the reviewer. |
| --- | --- |
namestringThe reviewer's profile name.linkstringA link to the reviewer's profile page on the Amazon domain.idstringThe reviewer profile ID. Can be specified as a request parameter to a type=reviewer\_profile request to view this reviewers public profile.| Manufacturer Reply Object | The Manufacturer Reply object contains details of product manufacturer's reply to the customer review. |
| --- | --- |
bodystringAny further comments about the product being reviewed, i.e. "Item will come repackaged."dateobject| Date Object | The date object contains details about the date of the manufacturer's reply. |
| --- | --- |
rawstringThe raw date as retrieved from the Amazon page.utcstringThe date of the manufacturer's reply, parsed from the raw date, in ISO 8601 format. If Rainforest API cannot parse the raw date then this property will be null.profileobject| Profile Object | The profile object contains details about the manufacturer's profile on the Amazon domain. |
| --- | --- |
namestringThe manufacturer's profile name.linkstringA link to the manufacturer's profile page on the Amazon domain.idstringThe manufacturer profile ID. Can be specified as a request parameter to a type=reviewer\_profile request to view this manufacturers public profile. |
| top\_positive | object | The most helpful positive customer review.The properties of the top\_positive object are identical to the Review object above. |
| top\_critical | object | The most helpful critical customer review.The properties of the top\_critical object are identical to the Review object above. |
| product | object | An object containing details of the product (in so far as those details are shown on the Customer Reviews page). For full product details you should issue a request with type=product to retrieve details from the product page.titlestringThe product name.linkstringThe product page link.is\_primebooleanDetermines whether the product is Prime-eligible or not.imagestringA link to the image of the product.asinstringThe Amazon product ID (ASIN) for the product.sub\_titleobject| Subtitle Object | The subtitle object contains details of the information shown in the subtitle directly underneath the product title. |
| --- | --- |
textstringThe text of the subtitle - typically the brand name of the product i.e. "Samsung".linkstringThe link of the subtitle - typically to the manufacturers page on the Amazon domain.attributesarray| Attributes Array | The attributes array contains details of the product attributes as shown underneath the product title on the Customer Reviews page. |
| --- | --- |
namestringThe name of the product attribute i.e. "Capacity".valuestringThe value of the product attribute i.e. "128 GB".attributes\_flatstringA comma seperated representation of the attributes array, useful when using CSV output using output=csv where the nested attributes array cannot be represented in CSV format.priceobject| Price Object | The price object contains details about the products pricing, as shown underneath the product title on the Customer Reviews page. |
| --- | --- |
symbolstringThe currency symbol, i.e. $ for USD.valuenumberThe price of the Offer.currencystringThe currency of the Offer as a ISO 4217 currency code.rawstringThe raw price as displayed on the Offer listing.shippingobject| Shipping Object | The shipping object contains details about the products shipping, as shown underneath the product title on the Customer Reviews page. |
| --- | --- |
rawstringThe raw shipping text as shown on the customer reviews page. |
| summary | object | An object containing a summary of all reviews for the product, as shown at the top-left of the Customer Reviews page.ratingnumberThe overall rating of the product, out of 5.ratings\_totalnumberThe total number of customer ratings the product has received.reviews\_totalnumberThe total number of customer reviews the product has received.reviews\_positivenumberThe total number of positive reviews the product has received.reviews\_criticalnumberThe total number of critical reviews the product has received.rating\_breakdownobjectAn object containing the total number of customer ratings the product has received, per star rating. |
| pagination | object | An object containing details of the current Reviews page and the total number of Reviews pages that are available. To paginate you should specify the page number in your request's page parameter.current\_pagenumberThe current page number.total\_pagesnumberThe total number of pages available.reviews\_totalnumberThe total number of reviews across all pages.startnumberThe starting index of reviews returned in this request.endnumberThe ending index of reviews returned in this request. |
Next Steps

* [Reviews Parameters](/docs/product-data-api/parameters/reviews)
