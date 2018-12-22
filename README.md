# Findex-api-doc

# General API information
 * The base endpoint is: https://api.findex.pro
 *  200 The requested action was received and successfully processed by the server.
 *  400 Bad Request indicates that the request by the client was not processed, as the server could not understand what the client is asking for.
 *  500 Internal Server Error indicates that the request is valid, but the server is totally confused and the server is asked to serve some unexpected condition.



# General endpoints
### 1. Get Token list on Findex
```javascript
GET /v1/tokenList
```
#### Response:
```json
{
    code:200,
    data:{
        tokenList:[
            {
                "symbol":"EOS",
                "contract":"eosio.token",
                "tokenID":1,
                "precision":10000
            },
            {
                "symbol":"ADD",
                "contract":"eosadddddddd",
                "tokenID":2,
                "precision":10000
            },
            .
            .
            .
        ]    
    }
}
```
### 2. Get token pair list on Findex
#### Response:
```json
{
    "code":200,
    "data":{
        "pairList":[
            {
                "quoteToken":"ADD",
                "baseToken":"EOS",
                "quoteContract":"eosadddddddd",
                "baseContract":"eosio.token",
                "pair":"ADD/EOS",
                "pairID":1
            },
            .
            .
            .
        ]
    }
}
```


### 3. Get token Pair
```javascript
GET /v1/pair
```
#### Parameters:
| Name        | Type   | Description |
| ----------- | ------ | ----------- |
| pairName    | STRING | String name of tokens adjacent by '_', like dice_eos |

#### Response:
```json
{
    "code":200,
    "data":{
        "pairs":[
                    {
                        "quoteToken":"DICE",
                        "baseToken":"EOS",
                        "quoteContract":"betdicetoken",
                        "baseContract":"eosio.token",
                        "pair":"DICE/EOS",
                        "pairID":15
                    },
                    [comment]: <> (The list may contains more elements if there are pairs with the same name.)
                ]
    }
}
```


### 4. Get token pair price on Findex
```javascript
GET /v1/pairPrice
```
#### Parameters:
| Name        | Type | Description |
| ----------- | -----| ----------- |
| id      | INT       | Id of the pair you are going to request  |


#### Response:
```json
{
  "code":200,
  "data": {
      "price":0.000055,
      "pair_id":"14"
  }
}
```
