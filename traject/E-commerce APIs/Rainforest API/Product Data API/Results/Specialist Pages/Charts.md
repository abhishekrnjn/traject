Charts Results
--------------

When making a request with the `type` [parameter](/docs/product-data-api/parameters/charts) set to `type=charts` Rainforest API will return Charts results for given Charts page `url`.

Charts results are retrieved from the [charts page](https://www.amazon.com/charts) on Amazon.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/charts.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Charts PageAn example of the JSON object returned from a Charts request is shown below:

{"request\_info":{...}"request\_metadata":{...}"request\_parameters":{...}"charts\_results":[...]"chart\_info":{...}}CopyRainforest API returns the following properties for Charts requests:

| Property | Type | Description |
| chart\_results | array | An array containing details of the products in the chart. Each object in the array contains the following properties:positionnumberThe position of the product in the chart.weeks\_on\_chartnumberThe number of weeks this product has been on the chart.last\_week\_positionnumberThe position the product has on this chart last week, if shown.titlestringThe title of the product.linkstringThe link to the product page.asinstringThe ASIN of the product.imagestringA link to the image of the product.ratingnumberThe overall rating of the product, out of 5.ratings\_totalnumberThe total number of customer ratings the product has received.authorstringThe author of the product, if available.agentstringThe agent for the product, if available.publisherstringThe publisher of the product, if available. |
| chart\_info | object | An object containing information about the chart.titlestringThe title of the chart.typestringThe type of the chart i.e. "Most Read".categorystringThe category of the chart i.e. "Fiction".time\_periodstringThe time period of the chart. |
Next Steps

* [Charts Parameters](/docs/product-data-api/parameters/charts)
