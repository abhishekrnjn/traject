Deals Parameters
----------------

GET`/request`The Deals Parameters are applicable when making a request with `type=deals` to retrieve Lightning Deal / Daily Deals results for an Amazon lightning deals / daily deals / 'goldbox' page. The category of deals and Amazon domain are specified using the `category_id` and `amazon_domain` parameter. The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Deals results are retrieved from the [deals listing page](https://www.amazon.com/gp/goldbox) on Amazon.

  
:::hint



**Category IDs**  
You can retrieve category IDs for each `amazon_domain` using the [Categories API](/docs/categories-api/overview). Category IDs are also returned in the `categories` array in each `type=deals` [response](/docs/product-data-api/results/deals).  
  
Multiple category IDs can be supplied, comma seperated, in the `category_id` parameter. For example, to request deals for Beauty (`3760911`) and Electronics (`172282`) categories on `amazon.com` the parameters would be `category_id=3760911,172282&amazon_domain=amazon.com`.  
  
If you wish to retrieve Deals from the deals homepage for a given `amazon_domain`, simply omit the `category_id` parameter entirely.  
:::

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/deals.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Deals PageFor example, to request deals results for Electronics category ID of `172282` on `amazon.com` the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=deals&category_id=15684181&amazon_domain=amazon.com
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="deals" \
-d category_id="15684181" \
-d amazon_domain="amazon.com"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "deals",
  category_id: "15684181",
  amazon_domain: "amazon.com"
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
  'type': 'deals',
  'category_id': '15684181',
  'amazon_domain': 'amazon.com'
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
  'type' => 'deals',
  'category_id' => '15684181',
  'amazon_domain' => 'amazon.com'
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

Copy### Deals Parameters

The following parameters are available for all requests made when `type=deals`.

**Note** that the [common](/docs/product-data-api/parameters/common) `include_html=true`, `output=html`, `customer_zipcode` and `customer_location` parameters cannot be used when making Deals requests.

| Parameter | Required | Description |
| --- | --- | --- |
| category\_id | optional | A comma-seperated list of Deals category IDs to retrieve deals results from, as returned by the Categories API. Category IDs are also returned in the categories array in each type=deals response.Multiple category IDs can be supplied, comma seperated, in the category\_id parameter. For example, to request deals for Beauty (3760911) and Electronics (172282) categories on amazon.com the parameters would be category\_id=3760911,172282&amazon\_domain=amazon.com.If you wish to retrieve Deals from the deals homepage for a given amazon\_domain, simply omit the category\_id parameter entirely. |
| amazon\_domain | optional | The Amazon domain to retrieve Deals from for the category ID(s) specified in the category\_id parameter. For a full list of supported Amazon domains see Supported Amazon Domains. |
| deal\_types | optional | The types of deal to include. If you omit the deal\_types parameter then all deal types are included.Note multiple deal types can be specified, comma-separated.Valid values are:deal\_of\_the\_dayInclude deal-of-the-day deals.lightning\_dealInclude lightning deals.best\_dealInclude best-deal deals. |
| deal\_states | optional | The types of deal state to include. If you omit the deal\_states parameter then all deal states are included.Note multiple deal states can be specified, comma-separated.Valid values are:availableInclude available-state deals.upcomingInclude upcoming-state deals.expiredInclude expired-state deals. |
| sort\_by | optional | Determines the sort order of the deals returned.Valid values are:featuredSort by featured deals.discount\_low\_to\_highSort by discount, lowest discount first.discount\_high\_to\_lowSort by discount, highest discount first.price\_low\_to\_highSort by price, lowest price first.price\_high\_to\_lowSort by price, highest price first. |
| prime\_eligable | optional | Determines whether to filter to only Prime-eligable deals:Valid values are:trueFilter to only Prime-eligable deals.falseInclude all deals, regardless of whether they are Prime-eligable or not. |
| minimum\_rating | optional | Only include deals for products with a customer rating meeting the specified criteria. If you omit the minimum\_rating parameter deals for products with any rating are included. Valid values are:1\_and\_upInclude deals for products with a 1-star customer rating and upwards.2\_and\_upInclude deals for products with a 2-star customer rating and upwards.3\_and\_upInclude deals for products with a 3-star customer rating and upwards.4\_and\_upInclude deals for products with a 4-star customer rating and upwards. |
| page | optional | The current page of deals results to retrieve. Inspect the pagination.total\_pages property in the Deals results to see how many pages of deal results are available. |
| max\_page | optional | Use the max\_page parameter to get multiple pages of results in one request. The API will automatically paginate through pages and concatenate the results into one response.See the Pagination docs for more information. |
| url | optional | The Amazon deals page URL to retrieve deals results from. This parameter, as it specifies a URL, should itself be url encoded.Note using the url parameter for Deals requests is not recommended as due to the session and pagination characteristics of the Deals pages simply specifying the url can prove unreliable in all but the simplest use-cases. It is recommended that you use the category\_id and amazon\_domain parameters to specify your Deals request instead. |
Next Steps

* [Deals Results](/docs/product-data-api/results/deals)
