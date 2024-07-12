Questions Results
-----------------

When making a request with the `type` [parameter](/docs/product-data-api/parameters/questions) set to `type=questions` Rainforest API will return all Customer Questions for the product specified in either the `asin` and `amazon_domain` parameters or the `url` parameter.

Questions are retrieved from the [customer questions page](https://www.amazon.com/product-questions/B073JYC4XM) for a single product on Amazon.

![]()Questions & Answers PageAn example of the JSON object returned from a Questions request is shown below:

{"request\_info":{...}"request\_metadata":{...}"request\_parameters":{...}"product":{...}"questions":[...]"pagination":{...}}CopyRainforest API returns the following properties for Questions requests:

  
:::hint



**Paginating Results**  
Amazon returns 10 Questions & Answers per page. To request more questions issue additional requests incrementing the `page` [parameter](/docs/product-data-api/parameters/questions).  
:::

| Property | Type | Description |
| questions | array | An array of Question objects, containing each of the Customer Questions & Answers shown on the Customer Questions & Answers page. The Question object has the following properties:idstringThe unique, Amazon-assigned, ID of the question. This can be used by your app to flag whether you have previously processed this question on a prior request. You can pass this id in as the question\_id to a subsequent type=question\_answers request to retrieve all answers to the question, see question answers parameters for more information.titlestringThe question text.bodystringThe answer text. This is the most helpful answer, in the case of there being multiple answers to the question. To retrieve all answers you should issue a subsequent type=question\_answers request, see question answers parameters for more information.linkstringThe link to the question.helpful\_votesnumberThe number of helpful votes this question answer has received from other Amazon customers.total\_answersnumberThe total number answers this question has received. To retrieve all answers pass the question id in as the question\_id to a subsequent type=question\_answers, see question answers parameters for more information.| Date Object | The date object contains details about the date of the answer to the question. |
| --- | --- |
utcstringThe date of the question answer, parsed from the raw date, in ISO 8601 format.| Profile Object | The profile object contains details of the profile of the customer who answered the question. |
| --- | --- |
namestringThe customer who provided the answer's profile name.linkstringThe customer who provided the answer's profile page on the Amazon domain.idstringThe customer profile ID. Can be specified as a request parameter to a type=reviewer\_profile request to view this customers' public profile. |
| product | object | An object containing details of the product (in so far as those details are shown on the Customer Questions & Answers page). For full product details you should issue a request with type=product to retrieve details from the product page.titlestringThe product name.linkstringThe product page link.imagestringA link to the image of the product.asinstringThe Amazon product ID (ASIN) for the product.sub\_titleobject| Subtitle Object | The subtitle object contains details of the information shown in the subtitle directly underneath the product title. |
| --- | --- |
textstringThe text of the subtitle - typically the brand name of the product i.e. "Samsung". |
| pagination | object | An object containing details of the current Questions & Answers page and the total number of pages that are available. To paginate you should specify the page number in your request's page parameter.current\_pagenumberThe current page number.total\_pagesnumberThe total number of pages available. |
Next Steps

* [Questions Parameters](/docs/product-data-api/parameters/questions)
* [Question Answers Parameters](/docs/product-data-api/parameters/question-answers)
* [Question Answers Results](/docs/product-data-api/results/question-answers)
