Seller Products Results
-----------------------

The Seller Products Parameters are applicable when making a request with `type=seller_products` to retrieve seller product listing results for a single seller on Amazon - the seller is specified using either the `seller_id` and `amazon_domain` parameters or the `url` parameter (where the `url` parameter contains a link to an Amazon seller product listing page). The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Seller product listing results are retrieved from the [seller product listings page](https://www.amazon.com/s?me=A02211013Q5HP3OMSZC7W&marketplaceID=ATVPDKIKX0DER) for a single seller on Amazon. You can retrieve the `seller_id` value for a given seller from other Rainforest requests, such as `type=offers` requests.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/seller_products.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Seller Products PageAn example of the JSON object returned from an Seller Products request is shown below:

{"request\_info":{...}"request\_metadata":{...}"request\_parameters":{...}"seller\_products":[...]"refinements":{...}"pagination":{...}}CopyRainforest API returns the following properties for Seller Products requests:

| Property | Type | Description |
| seller\_products | array | An array of Seller Product objects, containing each of the seller product results shown on the seller products listing page. The Seller Product object has the following properties:positionnumberThe position of the result on the seller product listing page.titlestringThe product name.asinstringThe Amazon product ID (ASIN) for the product.linkstringThe product page link.is\_primebooleanDetermines whether the product is Prime-eligible or not.imagestringA link to the image of the product.add\_on\_itemobject| Add-On Item Object | The add-on item object is present when the item is part of the Amazon 'add-on item' program. The property will be omitted if the product is not an add-on item. |
| --- | --- |
is\_add\_on\_itembooleanTrue/false indicating whether the product is an add-on item.bestsellerobject| Bestseller Object | An object containing details of whether the product is a bestseller and if so, in which category. The bestseller object has the following properties: |
| --- | --- |
categorystringThe name of the category (i.e. "Toys & Games") in which this product is a bestseller.ratingnumberThe overall rating of the product, out of 5.ratings\_totalnumberThe total number of customer ratings the product has received.reviews\_totalnumberThe total number of customer reviews the product has received.pricesarray| Prices Array | The prices array contains details about the products pricing, as shown underneath the product title. It is an array of price objects, the properties of which are described below: |
| --- | --- |
symbolstringThe currency symbol, i.e. $ for USD.valuenumberThe price of the Offer.currencystringThe currency of the Offer as a ISO 4217 currency code.rawstringThe raw price as displayed on the Offer listing.namestringThe name of the price if applicable, for example "Kindle", "Hardcover".priceobjectA price object representing the first item in the prices array. This is normally the "main" price for the product and is included as a convienience to make extracting the main price easier. |
| refinements | object | An object containing details of the available refinements for the given seller products results. These allow you to refine your request by values such as "Reviews rating 4 and over", "price range" and "brand". To refine your seller product results by a given refinement value you should specify refinement values, comma seperated, in your request's refinements parameter.Refinement values are dynamic and change by category area. If you wish to use refinements you should first issue a type=seller\_products request without specifying any refinements to retrieve a master list of the avaialble refinements for the given seller. You can then cache these refinement values for use on subsequent requests.The refinements object has a property name for each refinement that is available. This property contains an array showing the full-text refinement name and an value. It is this value that you should specify, comma seperated, in your request's refinements parameter.namestringThe full-text name of the refinement, for example "Brand".valuestringThe value of the refinement, you should specify the refinement value(s), comma seperated, in your request's refinements parameter.linkstringThe link shown for the refinement, you can use the link in a new type=seller\_products request's url parameter to navigate to the seller products results filtered by this refinement. |
| pagination | object | An object containing details of the current seller products listing page and the total number of pages that are available.current\_pagenumberThe current page number.total\_pagesnumberThe total number of pages available. |
Next Steps

* [Seller Products Parameters](/docs/product-data-api/parameters/seller-products)