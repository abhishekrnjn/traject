Formats & Editions Results
--------------------------

When making a request with the `type` [parameter](/docs/product-data-api/parameters/formats-editions) set to `type=formats_editions` Rainforest API will return data from the Formats & Editions popup (typically shown on books and collectables product pages to list all of the ASINs of different formats of the current ASIN) for the product specified in either the `asin` and `amazon_domain` parameters or the `url` parameter.

Formats & Editions data is retrieved from the [Formats & Editions popup](https://www.amazon.com/dp/B00B1GBS9O?th=1&psc=1) for a single product on Amazon.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/formats_editions.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Formats & Editions PageAn example of the JSON object returned from a Formats & Editions request is shown below:

{"formats\_editions":[...]"pagination":{...}}CopyRainforest API returns the following properties for Formats & Editions requests:

  
:::hint



**Paginating Results**  
Amazon returns 10 Formats & Editions per page. To request more formats & editions issue additional requests incrementing the `page` [parameter](/docs/product-data-api/parameters/formats-editions).  
  
**Note** you should inspect the `pagination.has_next_page` property to determine if another page is available.  
:::

| Property | Type | Description |
| formats\_editions | array | An array of Formats & Editions objects, containing each of the Formats & Editions shown on the Formats & Editions popup. The Formats & Editions object has the following properties:positionnumberThe position (1-based) of the format/edition on the current page.titlestringThe title of the format/edition.linkstringA link to the product page for the format/edition ASIN.asinstringThe ASIN of the format/edition.imagestringAn image URL to the image of the format/edition, if shown.ratingnumberAn rating of the image of the format/edition, if shown.ratings\_totalnumberAn total number of customer ratings the format/edition has received, if shown.specificationsarrayAn array of specifications containing name and value properties for each of the specifications for the format/edition.editionstringAn name of the edition, if shown.formatstringAn name of the format, if shown.publication\_datestringAn publication date of the format/edition, if shown.priceobject| Price Object | The price object contains details about the format/editions pricing. |
| --- | --- |
symbolstringThe currency symbol, i.e. $ for USD.valuenumberThe price of the format/edition.currencystringThe currency of the format/edition as a ISO 4217 currency code.rawstringThe raw price as displayed on the format/edition. |
| pagination | object | An object containing details of the current Formats & Editions page and whether a next page is available. To paginate you should specify the page number in your request's page parameter.current\_pagenumberThe current page number.has\_next\_pagebooleanSet to true if a next page of results is available. |
Next Steps

* [Formats & Editions Parameters](/docs/product-data-api/parameters/formats-editions)
