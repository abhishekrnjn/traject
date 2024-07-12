Bestsellers Parameters
----------------------

GET`/request`The Bestsellers Parameters are applicable when making a request with `type=bestsellers` to retrieve Bestseller results from an Amazon bestsellers page - the bestsellers page is specified either using the `category_id` and `amazon_domain` parameters (where `category_id` is a Category ID returned from the [Categories API](/docs/categories-api/overview), or by using the `url` parameter. The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Note that, if using the `url` parameter it should be url-encoded.

Bestsellers results are retrieved from the [bestsellers listing page](https://www.amazon.com/Best-Sellers-Appliances/zgbs/appliances/ref=zg_bs_nav_0) on Amazon. Rainforest supports all types of Amazon Bestseller pages, [bestsellers](https://www.amazon.com/Best-Sellers-Appliances/zgbs/appliances/ref=zg_bs_nav_0), [new releases](https://www.amazon.com/gp/new-releases/appliances/ref=zg_bsnr_nav_0), [movers & shakers](https://www.amazon.com/gp/movers-and-shakers/appliances/ref=zg_bsms_nav_0), [most wished for](https://www.amazon.com/gp/most-wished-for/appliances/ref=zg_mw_nav_0) and [gift ideas](https://www.amazon.com/gp/most-gifted/appliances/ref=zg_mg_nav_0).

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/bestsellers.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Bestsellers PageFor example, to request Bestsellers results for the "Appliances" bestsellers page, using `category_id=bestsellers_appliances` on `amazon_domain=amazon.com`, the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=bestsellers&category_id=bestsellers_appliances&amazon_domain=amazon.com
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="bestsellers" \
-d amazon_domain="amazon.com" \
-d category_id="bestsellers_appliances"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "bestsellers",
  amazon_domain: "amazon.com",
  category_id: "bestsellers_appliances"
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
  'type': 'bestsellers',
  'amazon_domain': 'amazon.com',
  'category_id': 'bestsellers_appliances'
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
  'type': =>'bestsellers',
  'amazon_domain' => 'amazon.com',
  'category_id' => 'bestsellers_appliances'
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

Copy### Bestsellers Parameters

The following parameters are available for all requests made when `type=bestsellers`.

| Parameter | Required | Description |
| --- | --- | --- |
| category\_id | optional | A category ID to retrieve bestsellers results from. You must supply a category\_id returned from the Categories API in to the category\_id parameter. |
| amazon\_domain | optional | The Amazon domain to retrieve bestsellers results from. For a full list of supported Amazon domains see Supported Amazon Domains. |
| url | optional | The Amazon Bestsellesr results page URL to retrieve bestsellers results from.Note: The url parameter should be url-encoded.Note: Either the url or category\_id & amazon\_domain parameters can be used. |
| top\_free | optional | Set to true to retrieve the "Top 100 Free" version of the specified Bestsellers category\_id or url. See screenshot below for how the Top 100 Paid / Top 100 Free bestsellers for a given category are displayed on the Amazon site.Note: Not every Bestsellers category has a "Top 100 Free" list. |
| page | optional | The current page of Bestsellers results to retrieve. Inspect the pagination.total\_pages property in the Bestsellers results to see how many pages of Bestsellers results are available. |
| max\_page | optional | Use the max\_page parameter to get multiple pages of results in one request. The API will automatically paginate through pages and concatenate the results into one response.See the Pagination docs for more information. |
Next Steps

* [Bestsellers Results](/docs/product-data-api/results/bestsellers)
