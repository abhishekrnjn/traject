Reviews Parameters
------------------

GET`/request`The Reviews Parameters are applicable when making a request with `type=reviews` to retrieve customer Reviews for a single product on Amazon - the product is specified using either the `asin` and `amazon_domain` parameters or the `url` parameter (where the `url` parameter contains a link to an Amazon reviews page). The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Reviews are retrieved from the [customer reviews page](https://www.amazon.com/product-reviews/B073JYC4XM) for a single product on Amazon.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/reviews.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Customer Reviews Page  
:::hint



**Lookup an ASIN by GTIN / ISBN / UPC / EAN**  
Rainforest API can automatically convert GTIN/ISBN/UPC/EAN codes to ASINs and return Reviews data for that GTIN. For details of how to lookup Amazon product details by GTIN/ISBN/UPC/EAN please see refer to the [guide](/docs/product-data-api/reference/gtin-upc-ean-to-asin).  
  
Note that Rainforest will cache the GTIN-to-ASIN mapping for 2 months. To force a new GTIN lookup (for example, if you suspect the existing mapping is stale), use the `skip_gtin_cache=true` request parameter (note that using `skip_gtin_cache=true` decrements 2 credits from your balance, instead of 1).  
:::

  
:::hint



**Reviews on Audible Domains**  
When specifying an Audible domain in a `type=reviews` request - i.e. `amazon_domain=audible.com`, the reviews are retrieved from the **Amazon Reviews** for the given ASIN, rather than the Audible Reviews.  
  
![](https://apiimages.imgix.net/rainforestapi/images/png/docs/audible_amazon_reviews.png?auto=format&ixlib=react-9.5.1-beta.1&w=250)  
:::

For example, to request all "critical" (i.e. negative) customer Reviews, sorted by "most recent", for the ASIN `B073JYC4XM` on `amazon.com` the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=reviews&amazon_domain=amazon.com&asin=B073JYC4XM&review_stars=all_critical&sort_by=most_recent
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="reviews" \
-d amazon_domain="amazon.com" \ 
-d asin="B073JYC4XM" \
-d review_stars="all_critical" \ 
-d sort_by="most_recent"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "reviews",
  amazon_domain: "amazon.com",
  asin: "B073JYC4XM",
  review_stars: "all_critical",
  sort_by: "most_recent"
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
  'review_stars': 'all_critical',
  'sort_by': 'most_recent'
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
  'review_stars' => 'all_critical',
  'sort_by' => 'most_recent'
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

Copy### Reviews Parameters

The following parameters are available for all requests made when `type=reviews`.

| Parameter | Required | Description |
| --- | --- | --- |
| amazon\_domain | optional | The Amazon domain to retrieve Reviews for the product specified in the asin parameter from. For a full list of supported Amazon domains see Supported Amazon Domains.Note: If the amazon\_domain and asin parameters are supplied then the url parameter is ignored. |
| asin | optional | The Amazon ASIN (product ID) to retrieve Reviews for. Used in combination with the amazon\_domain parameter.Note: If the asin and amazon\_domain parameters are supplied then the url parameter is ignored. |
| gtin | optional | A GTIN, ISBN, UPC or EAN code to retrieve results for. Internally Rainforest will first convert the GTIN/ISBN/UPC/EAN to an Amazon ASIN, then retrieve the results for that ASIN from Amazon. Used in combination with the amazon\_domain parameter.Note: If the gtin and amazon\_domain parameters are supplied then the url parameter is ignored. |
| skip\_gtin\_cache | optional | By default Rainforest will cache the GTIN-to-ASIN mapping for 2 months. To force a new GTIN lookup (for example, if you suspect the existing mapping is stale), use the skip\_gtin\_cache=true request parameter (note that using skip\_gtin\_cache=true decrements 2 credits from your balance, instead of 1). |
| url | optional | The Amazon product-page URL to retrieve Reviews from.Note: If the url parameter is supplied then the amazon\_domain and asin parameters are ignored. |
| reviewer\_type | optional | The type of reviewer to retrieve reviews from. Valid values are:verified\_purchaseInclude reviews by Amazon Verified Purchasers only.allInclude all reviews, regardless of whether they are from Amazon Verified Purchasers or not. |
| review\_stars | optional | The star rating of reviews to retrieve. Valid values are:all\_starsInclude reviews with any star rating.five\_starInclude reviews with a 5 star rating.four\_starInclude reviews with a 4 star rating.three\_starInclude reviews with a 3 star rating.two\_starInclude reviews with a 2 star rating.one\_starInclude reviews with a 1 star rating.all\_positiveInclude all positive reviews.all\_criticalInclude critical reviews. |
| review\_formats | optional | The type of reviewer to retrieve reviews from. Valid values are:all\_formatsInclude reviews of any product format/variant.current\_formatInclude reviews relating specifically to the current format/variant. |
| review\_media\_type | optional | Filter the reviews to those containing a specific media type. Valid values are:all\_reviewsInclude reviews with text, images or video.media\_reviews\_onlyInclude only reviews containing images or video. |
| sort\_by | optional | Determines the sort order of reviews to return. Valid values are:most\_helpfulReturns reviews with the most helpful reviews first.most\_recentReturns reviews in date order, with the most recent first. |
| global\_reviews | optional | Determines whether Global Reviews are included, or not Global Reviews are reviews from other Amazon domains outside of the Amazon domain specified in the request. Valid values are:trueThe default, Global Reviews are included in the results.falseGlobal reviews are excluded from the results. |
| search\_term | optional | A search term to use to search reviews. |
| show\_different\_asins | optional | Sometimes Amazon will return Reviews from ASINs other than the ASIN supplied in the asin request parameter (for example, when the original ASIN is out of stock). show\_different\_asins controls whether you want these other-ASIN review results returned, or not. Can be set to true (the default) to include reviews from other ASINs, or false to hide reviews from ASINs other than the ASIN supplied in the asin parameter. Note that if you supply a url instead of asin in your request this parameter is ignored.Note in the event of show\_different\_asins=false and the ASIN shown by Amazon being different from the requested ASIN, then all fields apart from product will be removed from the response. |
| page | optional | The current page of reviews to retrieve. Inspect the pagination.total\_pages property in the Reviews results to see how many pages of reviews are available.Note that the maximum number of reviews pages served by Amazon is 500. |
| max\_page | optional | Use the max\_page parameter to get multiple pages of results in one request. The API will automatically paginate through pages and concatenate the results into one response.See the Pagination docs for more information. |
| review\_id | optional | A single Review ID, as returned by a prior type=reviews request, to retrieve. Useful if you wish to check for the presence of a single review. Use in combination with the amazon\_domain parameter. |
Next Steps

* [Reviews Results](/docs/product-data-api/results/reviews)
