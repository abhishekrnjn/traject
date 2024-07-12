Stock Estimation Results
------------------------

When making a request with the `type` [parameter](/docs/product-data-api/parameters/stock-estimation) set to `type=stock_estimation` Rainforest API will return information about the stock level of the given `asin` from the shopping cart.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/stock_estimation.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Stock Estimation ResultAn example of the JSON object returned from a Stock Estimation request is shown below:

{"request\_info":{...}"request\_metadata":{...}"request\_parameters":{...}"stock\_estimation":{...}}Copy  
:::hint



**Products that Require Login**  
For some ASINs Amazon will require the user to be logged in to their Amazon account to add the product to the cart.  
  
In these instances Rainforest will be unable to provide stock estimation data. You can determine whether this is the case by inspecting the `stock_estimation.requires_login = true` property of the response.  
:::

Rainforest API returns the following properties for Stock Estimation requests:

| Property | Type | Description |
| stock\_level | number | The stock level of the product as shown on the shopping cart page. Note that this value could be influenced by a number of factors such as a maximum purchase quantity allowed by the seller or availability of the product at the seller. You should inspect the message property as this will show any alerts or messages shown on the shopping cart page also. |
| message | string | The message shown above the shopping cart - this could contain information about the stock level. For example, the message could indicate that the stock level shown is the maximum purchase quantity allowed by the seller, rather than the maximum number in stock. |
| availability\_message | string | The availability message shown above the shopping cart (i.e. Ships in 2-3 weeks. |
| has\_stock\_estimation | boolean | Set to false when Rainforest cannot generate a stock estimation. Typically this property is set to false when the ASIN is shown as "Currently Unavailable" on the Product Detail Page and therefore a stock estimation cannot be generated as the product cannot be added to the Cart. |
| price | object | A price object showing price and currency information for the product. |
| min\_quantity | number | The minimum purchase quantity for the product, as shown on the shopping cart page. |
| in\_stock | boolean | Whether the product is indicated as being in-stock on the shopping cart page. |
| is\_prime | boolean | Whether the product is indicated as being Prime-eligable as shown on the shopping cart page. |
| asin | string | The ASIN of the product as returned from the shopping cart page. |
| offer\_id | string | The Offer ID of the product offer as returned from the shopping cart page. |
| requires\_login | boolean | For some ASINs Amazon will require the user to be logged in to their Amazon account to add the product to the cart. In these instances Rainforest will be unable to provide stock estimation data. When this is the case requires\_login will be set to true. |
| Seller Object | The seller object contains details about the seller providing the Offer for this stock estimation request. Only shown for third party marketplace sellers. |
| --- | --- |
| name | string | The name of the seller of the Offer. |
| id | string | The ID of the seller of the Offer. |
| link | string | A link to the sellers shopfront on Amazon (for third party sellers). |
Next Steps

* [Stock Estimation Parameters](/docs/product-data-api/parameters/stock-estimation)
