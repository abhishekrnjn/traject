Sales Estimation Results
------------------------

When making a request with the `type` [parameter](/docs/product-data-api/parameters/sales-estimation) set to `type=sales_estimation` Rainforest API will return estimated sales for the given `asin` or `bestseller_rank`.

For full details of how Rainforest sales estimations are constructed and the methodology behind them please review the [sales estimation parameters](/docs/product-data-api/parameters/sales-estimation).

An example of the JSON object returned from a Sales Estimation request is shown below:

{"request\_info":{...}"request\_metadata":{...}"request\_parameters":{...}"sales\_estimation":{...}}Copy  
:::hint



**Note** if it is not possible for Rainforest to retrieve a sales estimation for a given `asin` or `bestseller_rank` request parameter (for example, because the product is ranked very low and Rainforest does not have sufficient data to perform a prediction) then no sales estimation will be returned.  
:::

Rainforest API returns the following properties for Sales Estimation requests:

| Property | Type | Description |
| sales\_estimation | object | | Sales Estimation Object | An object containing the sales estimation result. |
| --- | --- |
monthly\_sales\_estimatestringThe estimated monthly unit sales of the asin or bestseller\_rank specified in the sales estimation request. For details of the methodology Rainforest usees in generating sales estimations please review the sales estimation parameters.weekly\_sales\_estimatestringThe estimated weekly unit sales of the asin or bestseller\_rank specified in the sales estimation request. For details of the methodology Rainforest usees in generating sales estimations please review the sales estimation parameters.bestseller\_rankstringThe bestseller rank used by Rainforest in generating the sales estimation data.sales\_estimation\_categorystringThe sales estimation category used to perform the sales estimation prediction. Sales estimation categories are the top-level Amazon category that the given asin ranks in. For a full list of sales estimation categories see the sales estimation categories reference.has\_sales\_estimationbooleanTrue / false depending on whether sufficient data exists for Rainforest to generate a sales estimation. Rainforest sales estimation works using an internal algorithm utilizing signals from an ASIN's product page, bestseller rank, reviews, search result rankings and known sales datapoints to generate estimated weekly and monthly sales volumes. Rainforest must have sufficient datapoints available in order to generate a sales estimation.messagestringWhere has\_sales\_estimation=false then message contains an full-text explaination of why a sales estimation was not available for the given request parameters. |
Next Steps

* [Sales Estimation Parameters](/docs/product-data-api/parameters/sales-estimation)
* [Sales Estimation Categories](/docs/product-data-api/reference/sales-estimation-category-names)
