Author Page
-----------

When making a request with the `type` [parameter](/docs/product-data-api/parameters/author-page) set to `type=author_page` Rainforest API will return data from the author page for the author asin specified in either the `asin` and `amazon_domain` parameters or the `url` parameter.

Author page data is retrieved from the [author page](https://www.amazon.com/kindle-dbs/entity/author/B000APVZ7W) for a single author on Amazon.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/authors_page.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Author PageAn example of the JSON object returned from a Author Page request is shown below:

{"request\_info":{...}"request\_metadata":{...}"request\_parameters":{...}"author":{...}"similar\_authors":[...]"format\_ids":[...]"titles":[...]"pagination":{...}}CopyRainforest API returns the following properties for Author Page requests:

  
:::hint



**Paginating Results**  
To request more "titles" from the author page, issue additional requests incrementing the `page` [parameter](/docs/product-data-api/parameters/author-page).  
:::

| Property | Type | Description |
| author | object | An object containing details of the author.namestringThe name of the author.imagestringA url to the author image.biographystringThe biography of the author. |
| format\_ids | array | An array containing the Format IDs for the current author page. Format IDs can be passed into a subsequent type=author\_page requests' format\_id parameter to limit the titles array to just titles of the given format.Note that Format IDs are dynamic and can change from author to author, hence it is necessary to retrieve the Format IDs from the results and pass in to a subsequent request.namestringThe name of the Format ID.valuestringA value of the Format ID to be passed into a subsequent type=author\_page requests' format\_id parameter. |
| similar\_authors | array | An array containing the similar authors, as shown on the author page. The similar\_authors array contains objects with the following properties:namestringThe name of the similar author.imagestringA url to the image of the similar author.linkstringA link to the similar author's author page.asinstringA author ASIN of the similar author. |
| titles | array | An array of author title objects, containing each of the titles shown on the author page. The Author Title object has the following properties:namestringThe name of the title.asinstringThe ASIN of the title.is\_bestsellerbooleanTrue/false depending on whether this title has the Bestseller flag shown.release\_datestringThe release date of the title.ratingnumberThe rating of the title.ratings\_totalnumberThe total number of ratings this title has received..pricesarray| Prices Array | The prices array contains details about the titles pricing. It is an array of price objects, the properties of which are described below: |
| --- | --- |
symbolstringThe currency symbol, i.e. $ for USD.valuenumberThe price of the title.currencystringThe currency of the title as a ISO 4217 currency code.rawstringThe raw price as displayed on the title listing.namestringThe name of the price if applicable, for example "Kindle", "Hardcover".priceobjectA price object representing the first item in the prices array. This is normally the "main" price for the product and is included as a convienience to make extracting the main price easier. |
| pagination | object | An object containing details of the current author page titles array pagination. To paginate you should specify the page number in your request's page parameter.current\_pagenumberThe current page number.total\_pagesnumberThe total number of pages available.current\_page\_linkstringA link to the current page of author titles.next\_page\_linkstringA link to the next page of author titles. |
Next Steps

* [Author Page Parameters](/docs/product-data-api/parameters/author-page)
