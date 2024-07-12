Charts Parameters
-----------------

GET`/request`The Charts parameters are applicable when making a request with `type=charts` to retrieve Charts results. The Charts page can be specified using the `url` parameter. The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Charts results are retrieved from the [charts page](https://www.amazon.com/charts) on Amazon.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/charts.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Charts PageFor example, to request Charts results for the URL `https://www.amazon.com/charts`, the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=charts&url=https%3A%2F%2Fwww.amazon.com%2Fcharts
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="charts" \
-d url="https%3A%2F%2Fwww.amazon.com%2Fcharts"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "charts",
  url: "https%3A%2F%2Fwww.amazon.com%2Fcharts"
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
  'type': 'charts',
  'url': 'https%3A%2F%2Fwww.amazon.com%2Fcharts'
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
  'type' => 'charts',
  'url' => 'https%3A%2F%2Fwww.amazon.com%2Fcharts'
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

Copy### Charts Parameters

The following parameters are available for all requests made when `type=charts`.

| Parameter | Required | Description |
| --- | --- | --- |
| url | optional | The Charts page URL to retrieve Charts results from. Be sure to URL-encode the url parameter. |
Next Steps

* [Charts Results](/docs/product-data-api/results/charts)
