Common Parameters
-----------------

GET`/request`The following parameters are used to configure your request to the Product Data API. They should be appended as querystring parameters to a `GET`HTTP request to the `/request` endpoint.

For example, to request critical customer reviews, without a manufacturer reply, for the ASIN `B073JYC4XM` on `amazon.com` the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=reviews&amazon_domain=amazon.com&asin=B073JYC4XM&review_stars=all_critical
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="reviews" \
-d amazon_domain="amazon.com" \ 
-d asin="B073JYC4XM" \
-d review_stars="all_critical"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "reviews",
  amazon_domain: "amazon.com",
  asin: "B073JYC4XM",
  review_stars: "all_critical"
}

// make the http GET request to Rainforest API
axios.get('https://api.rainforestapi.com/request', { params })
  .then(response => {

    // print the JSON response from Rainforest API
    console.log(JSON.stringify(response.data, 0, 2));

  }).catch(error => {
    // catch and print the error
    console.log(error);
  })
```

```
import requests
import json

# set up the request parameters
params = {
  'api_key': 'demo',
  'type': 'reviews',
  'amazon_domain': 'amazon.com',
  'asin': 'B073JYC4XM',
  'review_stars': 'all_critical'
}

# make the http GET request to Rainforest API
api_result = requests.get('https://api.rainforestapi.com/request', params)

# print the JSON response from Rainforest API
print(json.dumps(api_result.json()))
```

```
<?php
      
# set up the request parameters
$queryString = http_build_query([
  'api_key' => 'demo',
  'type' => 'reviews',
  'amazon_domain' => 'amazon.com',
  'asin' => 'B073JYC4XM',
  'review_stars' => 'all_critical'
]);

# make the http GET request to Rainforest API
$ch = curl_init(sprintf('%s?%s', 'https://api.rainforestapi.com/request', $queryString));
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_FOLLOWLOCATION, true);
# the following options are required if you're using an outdated OpenSSL version
# more details: https://www.openssl.org/blog/blog/2021/09/13/LetsEncryptRootCertExpire/
curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, false);
curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);
curl_setopt($ch, CURLOPT_TIMEOUT, 180);

$api_result = curl_exec($ch);
curl_close($ch);

# print the JSON response from Rainforest API
echo $api_result;

?>
```
  
:::::

Copy  
:::hint



**Request-Specific Parameters**  
Additional parameters are available depending on the type of request being made (as-determined by the `type` parameter). For example, if you make a request with `type=offers` then additional [Offers Parameters](/docs/product-data-api/parameters/offers), specific to `offers` requests, are available.  
:::

### Common Parameters

The following common parameters are required for all requests to the Product Data API.

| Parameter | Required | Description |
| --- | --- | --- |
| api\_key | required | The API key for your Rainforest API account. |
| type | required | The type of Amazon data to retrieve. The value of the type parameter determines which additional parameters are available. For example, if you make a request with type=reviews then additional Reviews Parameters, specific to reviews requests, are available.Valid values for type are:productRequest data from the product page for an asin or Amazon product page url. See additional Product Parameters.stock\_estimationRequest stock estimation data for a given asin. See additional Stock Estimation Parameters.sales\_estimationRequest sales estimation data given asin or bestseller\_rank. See additional Sales Estimation Parameters.bestsellersRequest bestsellers data for a given Bestsellers category. See additional Bestsellers Parameters.searchRequest search results data for a given keywords on specific Amazon sites. See additional Search Parameters.offersRequest product offers for an asin or Amazon product page url. See additional Offers Parameters.reviewsRequest customer reviews for an asin or Amazon product page url. See additional Reviews Parameters.review\_commentsRequest customer review comments for a given review\_id. See additional Review Comments Parameters.reviewer\_profileRequest reviewer profile data for a reviewer\_id or Amazon reviewer profile page url. See additional Reviewer Profile Parameters.categoryRequest data for a given Amazon category. See additional Category Parameters.also\_boughtRequest all of the products, including those behind the scroll, listed as "also bought with" in the also bought carousel on the product page. See additional Also Bought Parameters.seller\_profileRequest seller profile data for a seller\_id or Amazon seller profile page url. See additional Seller Profile Parameters.seller\_feedbackRequest seller customer feedback results for a seller\_id. See additional Seller Feedback Parameters.seller\_productsRequest product listings for products sold by an Amazon seller specified by a seller\_id or Amazon seller product listing page url. See additional Seller Products Parameters.questionsRequest questions & answers for an asin or Amazon product page url. See additional Questions Parameters.question\_answersRequest all answers (not just the default selected answer) for a question\_id or Amazon question answers page url. See additional Question Answers Parameters.autocompleteRequest all autocomplete suggestions. See additional Autocomplete Parameters.author\_pageRequest an author page for a given author asin or Amazon authors page url. See additional Author Page Parameters.storeRequest an brand store for a given store\_id or Amazon brand store page url. See additional Store Parameters.chartsRequest data from an Amazon Charts page for the given url. See additional Charts Parameters.asin\_to\_gtinRequest GTIN / EAN / UPC / ISBN values for a given asin on a given amazon\_domain. See additional ASIN to GTIN Parameters. Can be used for converting ASINS to GTIN / EAN / UPC / ISBN numbers in bulk.formats\_editionsRequest data from the "Formats & Editions" popup typically shown on books product pages for a given asin on a given amazon\_domain. See additional Formats and Editions Parameters.wishlistRequest data from Amazon wishlists for a given wishlist\_id on a given amazon\_domain. See additional Wishlist Parameters. |
| include\_html | optional | Determines whether raw HTML is included in the response (this can increase the size of the response). Can be set to true or false (the default).Note When adding requests with include\_html=true to a Collection the maximum number of requests is lower (100) because including the HTML within the response makes the Collection Result Sets much larger. The limit is in place to ensure Result Set files are of a manageable size. If you have need to run a large number of requests all with include\_html=true then simply split the requests across multiple 100-request Collections. |
| output | optional | Determines the format in which results are returned. Can be set to json (default) to get the results as structured JSON, htmlto get the raw html retrieved or csvto return the results in CSV format. When using csvyou can also use the csv\_fieldsparameter to specify which fields to return in the CSV. |
| csv\_fields | optional | Determines the fields that are returned when returning in csvmode (i.e. when the outputparameter is set to csv). Should be specified as a comma seperated list of fields (in nested field, dot notation, format). For more information on the csv\_fieldsparameter please see the CSV Fields Reference. |
| customer\_location | optional | Determines the location that Rainforest uses when retrieving pages from Amazon. This is useful, for example, for seeing details of how a product appears on amazon.com, to a customer located in a different country. Can be used to identify cross-border shipping data and opportunities. For more available values of customer\_location please see the Customer Locations Reference. If no value for customer\_location is supplied then Rainforest defaults to making the request from the country of the Amazon page requested - i.e. "France" for requests for pages from "amazon.fr". |
| customer\_zipcode | optional | Determines the specific customer zipcode or postal code location of the request. This is useful, for example, for seeing details highly localized listings such as Amazon Fresh.To use the customer\_zipcode parameter you must first setup the zipcode, for the given Amazon Domain, in the zipcodes section of the Dashboard.For more information please see the Customer Zipcode Reference.Note The customer\_zipcode parameter cannot be used in conjuction with the customer\_location parameter. |
| language | optional | Determines the display language Rainforest requests the Amazon page in. For languages Amazon support see Supported Languages. |
| currency | optional | Determines the currency Rainforest requests the Amazon page. For supported currency values for each Amazon domain see the Supported Currencies. |
| skip\_on\_incident | optional | Instructs the API to not serve requests when a parsing incident is detected. Valid values are all (where the API will not serve a response if a "degraded" or "major" parsing incident is live) and major\_only (where the API will not serve a response is a "major" parsing incident is live, but will if a "degraded service" parsing incident is live).You can view service status via the status page.Using skip\_on\_incident can be desirable if your system is making unsupervised requests to the API that you would like to gracefully fail in the event of an incident. |
| associate\_id | optional | Pass your Amazon Associate ID (your Amazon affiliate ID) and Rainforest will append your Associate ID to all Amazon links returned in all API responses (by appending the tag=YOURASSOCIATEID parameter to all returned Amazon links). |
| include\_fields | optional | A comma-seperated list JSON field names to include in the JSON object the API returns. You can specify the field names in dot notation - i.e. include\_fields=pagination will only include the the pagination property in the response JSON. Use include\_fields if you only want to include specific fields in the API's JSON response. |
| exclude\_fields | optional | A comma-seperated list of JSON field names to exclude from the JSON object the API returns. You can specify the field names in dot notation - i.e. exclude\_fields=pagination will remove the pagination property from the response JSON. Use exclude\_fields if there are specific fields you wish to exclude from the API's JSON response. |
Next Steps

* [Offers Parameters](/docs/product-data-api/parameters/offers)
* [Stock Estimation Parameters](/docs/product-data-api/parameters/stock-estimation)
* [Reviews Parameters](/docs/product-data-api/parameters/reviews)
* [Product Parameters](/docs/product-data-api/parameters/product)
* [Search Parameters](/docs/product-data-api/parameters/search)
* [Bestsellers Parameters](/docs/product-data-api/parameters/bestsellers)
* [Category Parameters](/docs/product-data-api/parameters/category)
* [Also Bought Parameters](/docs/product-data-api/parameters/also-bought)
* [Seller Profile Parameters](/docs/product-data-api/parameters/seller-profile)
* [Seller Feedback Parameters](/docs/product-data-api/parameters/seller-feedback)
* [Seller Products Parameters](/docs/product-data-api/parameters/seller-products)
* [Autocomplete Parameters](/docs/product-data-api/parameters/autocomplete)
* [Author Page Parameters](/docs/product-data-api/parameters/author-page)
