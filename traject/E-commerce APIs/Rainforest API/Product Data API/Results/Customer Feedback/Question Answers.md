Question Answers Results
------------------------

The Question Answers Parameters are applicable when making a request with `type=question_answers` to retrieve all answers for a single question on Amazon - the question is specified using either the `question_id` and `amazon_domain` parameters or the `url` parameter (where the `url` parameter contains a link to a question answers page). The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Question Answers are retrieved from the [customer question answers page](https://www.amazon.com/ask/questions/Tx2YPKCGKAORFA4/1) for a single question on Amazon.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/question_answers.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Question Answers PageAn example of the JSON object returned from a Question Answers request is shown below:

{"request\_info":{...}"request\_metadata":{...}"request\_parameters":{...}"question":{...}"product":{...}"answers":[...]"pagination":{...}}CopyRainforest API returns the following properties for Question Answers requests:

  
:::hint



**Paginating Results**  
Amazon returns a maximum of 10 answers per page. To request more answers issue additional requests incrementing the `page` [parameter](/docs/product-data-api/parameters/question-answers).  
:::

| Property | Type | Description |
| question | object | An object containing details of the question to which the answers relate.titlestringThe question title text.| Date Object | The date object contains details about the date the question was asked. |
| --- | --- |
rawstringThe raw date as retrieved from the Amazon page.utcstringThe date the question was asked, parsed from the raw date, in ISO 8601 format. If Rainforest API cannot parse the raw date then this property will be null. |
| answers | array | An array of Answer objects, containing each of the answers shown on the Question Answers page. The Answer object has the following properties:idstringThe unique, Amazon-assigned, ID of the answer.answerstringThe body text of the answer.helpful\_votesnumberThe number of helpful votes this answer has received from other Amazon customers.helpful\_votes\_out\_ofnumberThe total number of votes this answer has received from other Amazon customers, including non-helpful votes. Can be used to calculate the % of votes cast that were helpful votes to get a measure of how helpful this answer is.| Date Object | The date object contains details about the date of the answer. |
| --- | --- |
rawstringThe raw date as retrieved from the Amazon page.utcstringThe date of the answer, parsed from the raw date, in ISO 8601 format. If Rainforest API cannot parse the raw date then this property will be null.| Profile Object | The profile object contains details of the profile of the customer who provided the answer. |
| --- | --- |
namestringThe answerer's profile name.linkstringA link to the answerer's profile page on the Amazon domain.idstringThe answerer profile ID. Can be specified as a request parameter to a type=reviewer\_profile request to view this reviewers public profile. |
| product | object | An object containing details of the product (in so far as those details are shown on the Question Answers page). For full product details you should issue a request with type=product to retrieve details from the product page.titlestringThe product name.linkstringThe product page link.imagestringA link to the image of the product.asinstringThe Amazon product ID (ASIN) for the product. |
| pagination | object | An object containing details of the current Question Answers page and the total number of Question Answers pages that are available. To paginate you should specify the page number in your request's page parameter.current\_pagenumberThe current page number.total\_pagesnumberThe total number of pages available. |
Next Steps

* [Question Answers Parameters](/docs/product-data-api/parameters/question-answers)
