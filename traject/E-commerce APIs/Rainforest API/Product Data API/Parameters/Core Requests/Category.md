Category Parameters
-------------------

GET`/request`The Category Parameters are applicable when making a request with `type=category` to retrieve category results for an Amazon category. Categories can be specified either via passing an Amazon category URL in to the `url` parameter, or by passing a Category ID in to the `category_id` (where the `category_id` is returned from the [Categories API](/docs/categories-api/overview)) and an Amazon domain in to the `amazon_domain` parameter. The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Category results are retrieved from the [category listing page](https://www.amazon.com/s?bbn=16225009011&rh=n%3A%2116225009011%2Cn%3A502394%2Cn%3A281052) on Amazon.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/category.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Category Listing PageFor example, to request category results for [this category URL](https://www.amazon.com/s?bbn=16225009011&rh=n%3A%2116225009011%2Cn%3A502394%2Cn%3A281052), the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=category&url=https%3A%2F%2Fwww.amazon.com%2Fs%3Fbbn%3D16225009011%26rh%3Dn%253A%252116225009011%252Cn%253A502394%252Cn%253A281052
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="category" \
-d url="https://www.amazon.com/s?bbn=16225009011&rh=n%3A%2116225009011%2Cn%3A502394%2Cn%3A281052"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "category",
  url: "https://www.amazon.com/s?bbn=16225009011&rh=n%3A%2116225009011%2Cn%3A502394%2Cn%3A281052"
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
  'type': 'category',
  'url': 'https://www.amazon.com/s?bbn=16225009011&rh=n%3A%2116225009011%2Cn%3A502394%2Cn%3A281052'
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
  'type' => 'category',
  'url' => 'https://www.amazon.com/s?bbn=16225009011&rh=n%3A%2116225009011%2Cn%3A502394%2Cn%3A281052'
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

Copy### Category Parameters

The following parameters are available for all requests made when `type=category`.

| Parameter | Required | Description |
| --- | --- | --- |
| category\_id | optional | A category ID to retrieve results from. You may supply any arbitary value in the category\_id parameter however we recommend using a category ID returned from the Categories API as these are known-good category IDs from Amazon.Rainforest will use the category\_id in the following form: https://amazon\_domain/s?node=category\_id.Note that pagination for top-level categories is not supported by the Amazon sites. If you wish to iterate the contents of a category the recommended approach is to pick the lowest level categories to perform your iteration / pagination on. |
| amazon\_domain | optional | The Amazon domain to retrieve category results from. For a full list of supported Amazon domains see Supported Amazon Domains. |
| url | optional | The Amazon category results page URL to retrieve category results from. Be sure to URL-encode the url parameter.Note the url parameter is supplied, the category\_id parameter cannot be used (as the url itself defines the category ID used). |
| sort\_by | optional | Determines the sort order of category results to return. Valid values are:most\_recentSort category results by newest arrivals.price\_low\_to\_highSort category results by lowest to highest price.price\_high\_to\_lowSort category results by highest to lowest price.featuredSort category results by featured first.average\_reviewSort category results by average customer review. |
| page | optional | The current page of category results to retrieve. Inspect the pagination.total\_pages property in the Category results to see how many pages of category results are available. |
| max\_page | optional | Use the max\_page parameter to get multiple pages of results in one request. The API will automatically paginate through pages and concatenate the results into one response.See the Pagination docs for more information. |
| refinements | optional | A comma-seperated list of refinement values to filter the category results by. These allow you to refine your category results by values such as "Reviews rating 4 and over", "price range" and "brand".Refinement values are returned in the refinements array of each type=category result. Refinement values are dynamic and change by category area or search term used. If you wish to use refinements you should first issue a type=category request without specifying any refinements to retrieve a master list of the avaialble refinements for the given category area/search term. You can then cache these refinement values for use on subsequent requests.For example, to run a type=search request specifying two refinements with values p\_85/2470955011 and p\_36/2421886011 the value of the refinements parameter would be refinements=p\_85/2470955011,p\_36/2421886011Note that sometimes Amazon do not present a explicit refinement value and instead a link is returned. In this instance you should pass the link into the url request parameter of your type=category request to retrieve data from that refinement-filtered page. |
Next Steps

* [Category Results](/docs/product-data-api/results/category)
