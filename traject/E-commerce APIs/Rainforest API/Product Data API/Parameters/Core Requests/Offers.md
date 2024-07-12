Offers Parameters
-----------------

GET`/request`The Offers Parameters are applicable when making a request with `type=offers` to retrieve seller Offers for a single product on Amazon - the product is specified using either the `asin` and `amazon_domain` parameters or the `url` parameter (where the `url` parameter contains a link to an Amazon product offers page). The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Offers are retrieved from the offers listing popup window for a single product on Amazon.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/offers.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Offers Listing Page  
:::hint



**Lookup an ASIN by GTIN / ISBN / UPC / EAN**  
Rainforest API can automatically convert GTIN/ISBN/UPC/EAN codes to ASINs and return Product Offers data for that GTIN. For details of how to lookup Amazon product details by GTIN/ISBN/UPC/EAN please see refer to the [guide](/docs/product-data-api/reference/gtin-upc-ean-to-asin).  
  
Note that Rainforest will cache the GTIN-to-ASIN mapping for 2 months. To force a new GTIN lookup (for example, if you suspect the existing mapping is stale), use the `skip_gtin_cache=true` request parameter (note that using `skip_gtin_cache=true` decrements 2 credits from your balance, instead of 1).  
:::

For example, to request Prime-eligable Offers, for products in a New Condition, for the ASIN `B073JYC4XM` on `amazon.com` the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=offers&amazon_domain=amazon.com&asin=B073JYC4XM&offers_prime=true&offers_condition_new=true
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="offers" \
-d amazon_domain="amazon.com" \
-d asin="B073JYC4XM" \
-d offers_prime="true" \
-d offers_condition_new="true"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "offers",
  amazon_domain: "amazon.com",
  asin: "B073JYC4XM",
  offers_prime: "true",
  offers_condition_new: "true"
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
  'type': 'offers',
  'amazon_domain': 'amazon.com',
  'asin': 'B073JYC4XM',
  'offers_prime': 'true',
  'offers_condition_new': 'true'
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
  'type' => 'offers',
  'amazon_domain' => 'amazon.com',
  'asin' => 'B073JYC4XM',
  'offers_prime' => 'true',
  'offers_condition_new' => 'true'
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

Copy### Offers Parameters

The following parameters are available for all requests made when `type=offers`.

| Parameter | Required | Description |
| --- | --- | --- |
| amazon\_domain | optional | The Amazon domain to retrieve Offers for the product specified in the asin parameter from. For a full list of supported Amazon domains see Supported Amazon Domains.Note: If the amazon\_domain and asin parameters are supplied then the url parameter is ignored. |
| asin | optional | The Amazon ASIN (product ID) to retrieve Offers for. Used in combination with the amazon\_domain parameter.Note: If the asin and amazon\_domain parameters are supplied then the url parameter is ignored. |
| gtin | optional | A GTIN, ISBN, UPC or EAN code to retrieve results for. Internally Rainforest will first convert the GTIN/ISBN/UPC/EAN to an Amazon ASIN, then retrieve the results for that ASIN from Amazon. Used in combination with the amazon\_domain parameter.Note: If the gtin and amazon\_domain parameters are supplied then the url parameter is ignored. |
| skip\_gtin\_cache | optional | By default Rainforest will cache the GTIN-to-ASIN mapping for 2 months. To force a new GTIN lookup (for example, if you suspect the existing mapping is stale), use the skip\_gtin\_cache=true request parameter (note that using skip\_gtin\_cache=true decrements 2 credits from your balance, instead of 1). |
| url | optional | The Amazon product-page URL to retrieve Offers from.Note: If the url parameter is supplied then the amazon\_domain and asin parameters are ignored. |
| offers\_prime | optional | Limit the offers returned to just those that are Prime-eligible. Valid values are:trueOnly include offers that are Prime-eligible.falseInclude all offers, regardless of whether they are Prime-eligible or not. |
| offers\_free\_shipping | optional | Limit the offers returned to just those that have Free Shipping. Valid values are:trueOnly include offers that have Free Shipping.falseInclude all offers, regardless of whether they have Free Shipping or not. |
| offers\_condition\_new | optional | Limit the offers returned to just those that are of New Condition. Valid values are:trueOnly include offers that are New Condition.falseInclude all offers, regardless of their Condition. |
| offers\_condition\_used\_like\_new | optional | Limit the offers returned to just those that are of Used-Like-New Condition. Valid values are:trueOnly include offers that are Used-Like-New Condition.falseInclude all offers, regardless of their Condition. |
| offers\_condition\_used\_very\_good | optional | Limit the offers returned to just those that are of Used-Very-Good Condition. Valid values are:trueOnly include offers that are Used-Very-Good Condition.falseInclude all offers, regardless of their Condition. |
| offers\_condition\_used\_good | optional | Limit the offers returned to just those that are of Used-Good Condition. Valid values are:trueOnly include offers that are Used-Good Condition.falseInclude all offers, regardless of their Condition. |
| offers\_condition\_used\_acceptable | optional | Limit the offers returned to just those that are of Used-Acceptable Condition. Valid values are:trueOnly include offers that are Used-Acceptable Condition.falseInclude all offers, regardless of their Condition. |
| show\_different\_asins | optional | Sometimes Amazon will return Offers from ASINs other than the ASIN supplied in the asin request parameter (for example, when the original ASIN is out of stock). show\_different\_asins controls whether you want these other-ASIN offer results returned, or not. Can be set to true to include offers from other ASINs, or false (the default) to hide offers from ASINs other than the ASIN supplied in the asin parameter. Note that if you supply a url instead of asin in your request this parameter is ignored. |
| page | optional | The current page of Offers to retrieve. Inspect the pagination.total\_pages property in the Offers results to see how many pages of offers are available. |
| max\_page | optional | Use the max\_page parameter to get multiple pages of results in one request. The API will automatically paginate through pages and concatenate the results into one response.See the Pagination docs for more information. |
Next Steps

* [Offers Results](/docs/product-data-api/results/offers)
