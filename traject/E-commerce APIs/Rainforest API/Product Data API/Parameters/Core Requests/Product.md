Product Parameters
------------------

GET`/request`The Product Parameters are applicable when making a request with `type=product` to retrieve details of a single product on Amazon - the product is specified using either the `asin` and `amazon_domain` parameters or the `url` parameter (where the `url` parameter contains a link to an Amazon product page). The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Product details are retrieved from the [product page](https://www.amazon.com/dp/B073JYC4XM) for a single product on Amazon.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/product.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Product Page  
:::hint



**Lookup an ASIN by GTIN / ISBN / UPC / EAN**  
Rainforest API can automatically convert GTIN/ISBN/UPC/EAN codes to ASINs and return product data. For details of how to lookup Amazon product details by GTIN/ISBN/UPC/EAN please see refer to the [guide](/docs/product-data-api/reference/gtin-upc-ean-to-asin).  
  
Note that Rainforest will cache the GTIN-to-ASIN mapping for 2 months. To force a new GTIN lookup (for example, if you suspect the existing mapping is stale), use the `skip_gtin_cache=true` request parameter (note that using `skip_gtin_cache=true` decrements 2 credits from your balance, instead of 1).  
:::

For example, to request details for the ASIN `B073JYC4XM` on `amazon.com` the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=product&amazon_domain=amazon.com&asin=B073JYC4XM
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="product" \
-d amazon_domain="amazon.com" \ 
-d asin="B073JYC4XM"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "product",
  amazon_domain: "amazon.com",
  asin: "B073JYC4XM"
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
  'type': 'product',
  'amazon_domain': 'amazon.com',
  'asin': 'B073JYC4XM'
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
  'type' => 'product',
  'amazon_domain' => 'amazon.com',
  'asin' => 'B073JYC4XM'
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

Copy### Product Parameters

The following parameters are available for all requests made when `type=product`.

| Parameter | Required | Description |
| --- | --- | --- |
| amazon\_domain | optional | The Amazon domain to retrieve product details from for the product specified in the asin parameter. For a full list of supported Amazon domains see Supported Amazon Domains.Note: If the amazon\_domain and asin parameters are supplied then the url parameter is ignored. |
| asin | optional | The Amazon ASIN (product ID) to retrieve product details for. Used in combination with the amazon\_domain parameter.Note: If the asin and amazon\_domain parameters are supplied then the url parameter is ignored. |
| gtin | optional | A GTIN, ISBN, UPC or EAN code to retrieve results for. Internally Rainforest will first convert the GTIN/ISBN/UPC/EAN to an Amazon ASIN, then retrieve the results for that ASIN from Amazon. Used in combination with the amazon\_domain parameter.Note: If the gtin and amazon\_domain parameters are supplied then the url parameter is ignored. |
| skip\_gtin\_cache | optional | By default Rainforest will cache the GTIN-to-ASIN mapping for 2 months. To force a new GTIN lookup (for example, if you suspect the existing mapping is stale), use the skip\_gtin\_cache=true request parameter (note that using skip\_gtin\_cache=true decrements 2 credits from your balance, instead of 1). |
| include\_summarization\_attributes | optional | Determines whether Rainforest returns the summarization\_attributes and customers\_say properties as part of the product request. The summarization attributes are displayed next to the product reviews and typically show the rating, out of 5, a product has received for a specific attribute, for example "value for money" or "durability".When include\_summarization\_attributes=true a summarization\_attributes property containing the summarization attributes, and customers\_say property containing the summerization of review themes, is shown in the result.Note: When include\_summarization\_attributes=true 2 credits are charged instead of 1 for the request (this is due to the increased number of internal requests required to retrieve summarization attributes). |
| include\_a\_plus\_body | optional | Determines whether Rainforest includes the HTML of the A-Plus description section (typically under the heading "From the manufacturer") in the response. |
| include\_book\_description\_raw | optional | Determines whether raw HTML for the book\_description is included in the response (this can increase the size of the response). Can be set to true or false (the default). Only applies to ASINs that has a book\_description in their response. |
| url | optional | The Amazon product-page URL to retrieve product details from.Ensure that the url parameter is URL-encoded.Note: If the url parameter is supplied then the amazon\_domain and asin parameters are ignored. |
Next Steps

* [Product Results](/docs/product-data-api/results/product)
