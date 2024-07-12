Store Results
-------------

When making a request with the `type` [parameter](/docs/product-data-api/parameters/store) set to `type=store` Rainforest API will return Brand Store results for a Brand Store. The Brand Store can be specified either by the `url` parameter, or by a combination of the `store_id` and `amazon_domain` parameters. The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Brand Store results are retrieved from the [brand store page](https://www.amazon.com/stores/page/70F3122D-4966-4242-A8A6-871C8D7E6F8B) on Amazon.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/brand_store.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Brand Store PageAn example of the JSON object returned from a Brand Store request is shown below:

{"request\_info":{...}"request\_metadata":{...}"request\_parameters":{...}"store\_info":{...}"store\_results":[...]"categories":[...]"pagination":{...}}Copy  
:::hint



**Editorial Results**  
Store result pages can have different layouts and are not always a standard list of ASIN results. If a `store_result` has the `type=editorial` then the ASIN is being displayed as a graphic/creative, instead of a regular ASIN product listing. In this instance the `title` field is not available (as the text of the product title is shown in the creative image instead) and a `editorial_image` field containing the creative image is returned.  
:::

Rainforest API returns the following properties for Brand Store requests:

| Property | Type | Description |
| store\_info | object | An object containing details of the Brand Store.namestringThe name of the Brand Store, if shown.descriptionstringThe description of the Brand Store, if shown.logoobjectAn object containing link and title properties being the image URL link to the Brand Store logo, and the title associated with the logo image.hero\_imageobjectAn object containing a link property being a link to the hero (banner) image URL, if shown on the Brand Store page. |
| store\_results | array | An array containing details of the products shown on the Brand Store page. Each object in the array contains the following properties:titlestringThe title of the product, not available when type=editoriallinkstringThe link to the product page.asinstringThe ASIN of the product.imagestringA link to the image of the product.ratingnumberThe overall rating of the product, out of 5.ratings\_totalnumberThe total number of customer ratings the product has received.priceobjectA price object describing the price of the product.typenumberSet to editorial in the case of the ASIN result being shown as an "editorial" result (where the ASIN is described in a creative image, instead of a regular ASIN list) or regular in the case of the ASIN result being shown in a regular list.editorial\_imagenumberReturned when type=editorial (if available) and contains a link to the creative image for the ASIN result. |
| categories | array | An array containing details of the categories shown on the Brand Store page. Each object in the array contains the following properties:namestringThe name of the category (i.e. "Toys & Games").linkstringThe link to the Brand Store page category.is\_currentbooleanSet to true when the Brand Store category is the currently displayed one. |
| pagination | object | An object containing details of the current Brand Store page and the total number of pages that are available.current\_pagenumberThe current page number.total\_pagesnumberThe total number of pages available. |
Next Steps

* [Store Parameters](/docs/product-data-api/parameters/store)
