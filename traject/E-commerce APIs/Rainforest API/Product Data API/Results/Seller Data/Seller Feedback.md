Seller Feedback Results
-----------------------

The Seller Feedback Parameters are applicable when making a request with `type=seller_feedback` to retrieve seller customer feedback details for a seller on Amazon - the seller is specified using the `seller_id` and `amazon_domain` parameters. The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Seller feedback details are retrieved from the [feedback](https://www.amazon.com/sp?seller=A02211013Q5HP3OMSZC7W) section of the seller profile page. You can retrieve the `seller_id` value for a given seller from other Rainforest requests, such as `type=offers` requests.

A maximum of 5 seller feedback records can be returned per request. You can paginate through multiple pages of seller feedback records using the `page` parameter. Inspect the `pagination.has_next_page` property to determine whether there is a next page of results to retrieve.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/seller_feedback.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Seller Feedback ResultsAn example of the JSON object returned from an Seller Feedback request is shown below:

{"request\_info":{...}"request\_metadata":{...}"request\_parameters":{...}"seller\_feedback":[...]"pagination":{...}}CopyRainforest API returns the following properties for Seller Feedback requests:

| Property | Type | Description |
| seller\_feedback | array | | Seller Feedback Array | The seller feedback array contains feedback objects representing the customer feedback results for the current seller feedback page. The feedback object has the following properties: |
| --- | --- |
raternumberThe customer rating given with the feedback, out of 5.bodystringThe body text of the customer feedback.raterstringThe name of the customer giving the customer feedback about this seller.has\_responsebooleanWhether the feedback has received a seller response, or not.dateobject| Date Object | The date object contains details about the date of the feedback was left. |
| --- | --- |
rawstringThe raw date as retrieved from the feedback (an un-parsed string).utcstringThe date of the feedback, parsed from the raw date, in ISO 8601 format. If Rainforest API cannot parse the raw date then this property will be null. |
| pagination | object | An object containing details of the current Seller Feedback page and whether or not a next-page of results is available. To paginate you should check whether has\_next\_page=true and specify the next\_page number in a subsequent request's page parameter.current\_pagenumberThe current page number.has\_next\_pagebooleanWhether a next page is available, or not.next\_pagenumberThepage number of the next page. |
Next Steps

* [Seller Feedback Parameters](/docs/product-data-api/parameters/seller-feedback)
