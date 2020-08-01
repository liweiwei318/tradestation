Portfolio

Portfolio functions enable you to utilize figures specific to your own account in calculations. 
If applied to a symbol, the functions will not include its derivatives in the calculation.

The following limitations apply when using the GetAveragePrice, GetOpenPL, and GetQuantity functions:

They cannot be used on charts with a price type other than LAST (i.e., they won't work with MARK, ASK, or BID price types).
If applied to a futures product chart, they subscribe to the active contract data.
Note also that Portfolio functions can only be used with the following aggregation 
periods: 1 min, 2 min, 3 min, 4 min, 5 min, 10 min, 15 min, 20 min, 30 min, 1h, or 1 day. 
Time period for the aggregation of 1 day is limited to 1 year. 

Currently, the following Portfolio functions are available:

GetAveragePrice
GetNetLiq
GetOpenPL
GetQuantity
GetTotalCash

Refer to https://tlc.thinkorswim.com/center/reference/thinkScript/Functions/Portfolio
