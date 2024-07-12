Review Comments Results
-----------------------

When making a request with the `type` [parameter](/docs/product-data-api/parameters/review-comments) set to `type=review_comments` Rainforest API will return all Customer Review Comments for the Review ID specified using the `review_id`, `asin` and `amazon_domain` parameters.

Review comments are retrieved from the [customer reviews page](https://www.amazon.com/product-reviews/B073JYC4XM) for a single customer review for a single product on Amazon.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/review_comments.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Review Comments SectionAn example of the JSON object returned from a Review Comments request is shown below:

{"request\_info":{...}"request\_metadata":{...}"request\_parameters":{...}"review\_comments":[...]}CopyRainforest API returns the following properties for Review Comments requests:

  
:::hint



**Review Comments Count**  
Rainforest can retrieve up to 100 review comments per request. For tracking new comments the most common approach is to run a `type=review_comments` request with `sort_by=most_recent` set, to ensure you always retrieve the latest review comments.  
:::

| Property | Type | Description |
| review\_comments | array | An array of Review Comment objects, containing each of the Customer Review Comments shown on against the specified Customer Review. The Review Comment object has the following properties:idstringThe unique, Rainforest-generated, ID of the customer review comment. This can be used by your app to flag whether you have previously processed this review comment on a prior request.bodystringThe body text of the review comment.| Date Object | The date object contains details about the date of the review comment. |
| --- | --- |
rawstringThe raw date as retrieved from the Amazon page.utcstringThe date of the review comment, parsed from the raw date, in ISO 8601 format. If Rainforest API cannot parse the raw date then this property will be null.| Profile Object | The profile object contains details of the profile of the review comment author. |
| --- | --- |
namestringThe review comment authors' profile name.linkstringA link to the review comment authors' profile page on the Amazon domain.idstringThe review comment authors' profile ID. Can be specified as a request parameter to a type=reviewer\_profile request to view this authors public Amazon profile. |
Next Steps

* [Review Comments Parameters](/docs/product-data-api/parameters/review-comments)
