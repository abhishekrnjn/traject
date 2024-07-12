Autocomplete Parameters
-----------------------

GET`/request`When making a request with the `type` parameter set to `type=autocomplete` Rainforest API will return autocomplete suggestions for the search term specified in the `search_term` parameter, on the Amazon domain specified in the `amazon_domain` parameter.

You may scope your autocomplete request to an Amazon autocomplete alias (synonymous with a product area or top-level category) by specifying the alias using the `autocomplete_alias` parameter. The available `autocomplete_alias` values vary depending on the `amazon_domain` used. You can find a full list of all autocomplete aliaes, per Amazon-domain, in the [autocomplete aliases reference](/docs/product-data-api/reference/autocomplete-aliases).

![]()Autocomplete SuggestionsFor example, to request autocomplete suggestions for the search term `animal` on `amazon.com` using the autocomplete alias "Books" the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=autocomplete&amazon_domain=amazon.com&search_term=animal&autocomplete_alias=stripbooks
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="autocomplete" \
-d amazon_domain="amazon.com" \
-d search_term="animal" \
-d autocomplete_alias="stripbooks"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "autocomplete",
  amazon_domain: "amazon.com",
  search_term: "animal",
  autocomplete_alias: "stripbooks"
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
  'type': 'autocomplete',
  'amazon_domain': 'amazon.com',
  'search_term': 'animal',
  'autocomplete_alias': 'stripbooks',
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
  'type' => 'autocomplete',
  'amazon_domain' => 'amazon.com',
  'search_term' => 'animal',
  'autocomplete_alias' => 'stripbooks',
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

Copy### Autocomplete Parameters

The following parameters are available for all requests made when `type=autocomplete`.

| Parameter | Required | Description |
| --- | --- | --- |
| amazon\_domain | required | The Amazon domain to retrieve autocomplete details from for the search term specified in the search\_term parameter. For a full list of supported Amazon domains see Supported Amazon Domains. |
| search\_term | required | The search term to get autocomplete suggestions for. Used in combination with the amazon\_domain parameter. |
| autocomplete\_alias | optional | The alias to use to scope the autocomplete request. Autocomplete aliases can be thought of as the "category" area that the autocomplete request runs in. If none is specified then Rainforest will default to running the autocomplete request in the top-level "All Departments" autocomplete alias.For a full list of supported Autocomplete Aliases see Supported Autocomplete Aliases. |
Next Steps

* [Autocomplete Results](/docs/product-data-api/results/autocomplete)
