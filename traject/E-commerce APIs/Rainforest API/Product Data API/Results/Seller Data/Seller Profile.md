Seller Profile Results
----------------------

When making a request with the `type` [parameter](/docs/product-data-api/parameters/seller-profile) set to `type=seller_profile` Rainforest API will return details of seller specified in either the `seller_id` and `amazon_domain` parameters or the `url` parameter.

Seller profile details are retrieved from the [seller profile page](https://www.amazon.com/sp?seller=A02211013Q5HP3OMSZC7W) for a single seller on Amazon. You can retrieve the `seller_id` value for a given seller from other Rainforest requests, such as `type=offers` requests.

You can use subsequent [seller products](/docs/product-data-api/parameters/seller-products) and [seller feedback](/docs/product-data-api/parameters/seller-feedback) requests to retrieve iterate all of the products and customer feedback from a given seller.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/seller_profile.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Seller Profile PageAn example of the JSON object returned from an Seller Profile request is shown below:

{"request\_info":{...}"request\_metadata":{...}"request\_parameters":{...}"seller\_details":{...}"feedback\_summary":{...}"feedback":[...]}CopyRainforest API returns the following properties for Seller Profile requests:

| Property | Type | Description |
| seller\_details | object | | Seller Details Object | The seller details object contains address, contact and ratings details about the seller. |
| --- | --- |
namestringThe name of the seller.store\_linkstringA link to the sellers Amazon store.logostringThe link to the logo of the seller.phonestringThe phone number of the seller, if shown.emailstringThe email of the seller, if shown.ratingnumberThe rating of the seller, out of 5.ratings\_totalnumberThe total number of customer ratings the seller has received.ratings\_total\_percentagenumberThe total positive customer ratings percentage the seller has received.business\_namestringThe name of the business, if shown. This is typically shown as the businesses legal name, as opposed to the seller brand name shown in the name property.business\_addressstringThe address of the sellers' business, if shown on the seller profile page.business\_address\_rowsarrayThe address of the sellers' business presented as an array of strings for each line of the address, if shown on the seller profile page.about\_this\_sellerstringThis is a free-form text area populated by the seller describing the seller.detailed\_informationstringDetailed information about the seller. This is a free-form text area populated by the seller but is likely to contain their address and contact details. |
| feedback\_summary | object | | Feedback Summary Object | The feedback summary object gives a breakdown of the seller customer feedback received over the last 30 days, 90 days, 12 months and for the lifetime of the seller. Positive, neutral, negative and total count datapoints are available. |
| --- | --- |
thirty\_daysobjectAn object containing the positive\_percent, neutral\_percent, negative\_percent and count feedback the seller has received in the last 30 days.ninety\_daysobjectAn object containing the positive\_percent, neutral\_percent, negative\_percent and count feedback the seller has received in the last 90 days.twelve\_monthsobjectAn object containing the positive\_percent, neutral\_percent, negative\_percent and count feedback the seller has received in the last 12 months.lifetimeobjectAn object containing the positive\_percent, neutral\_percent, negative\_percent and count feedback the seller has received over the lifetime of the seller. |
| feedback | array | | Feedback Array | The feedback array contains the first page of customer feedback shown on the seller profile page. To retrieve further pages of customer feedback you should issue type=seller\_feedback requests. The feedback object has the following properties: |
| --- | --- |
ratingnumberThe customer rating given with the feedback, out of 5.bodystringThe body text of the customer feedback.raterstringThe name of the customer giving the customer feedback about this seller. |
Next Steps

* [Seller Profile Parameters](/docs/product-data-api/parameters/seller-profile)
