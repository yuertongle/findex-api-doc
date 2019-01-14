# Findex-api-doc

# General API information
 * The base endpoint is: https://api.findex.pro
 * 200 The requested action was received and successfully processed by the server.
 * 204 No Content represents the request is successfully processed, but has not returned any content.
 * 400 Bad Request indicates that the request by the client was not processed, as the server could not understand what the client is asking for.
 * 500 Internal Server Error indicates that the request is valid, but the server is totally confused and the server is asked to serve some unexpected condition.



# General endpoints
### 1. Get token list on Findex
```javascript
GET /v1/tokenList
```
#### Response(tokenList contains multiple elements):
```json
{
    "code":200,
    "data":{
        "tokenList":[
            {
                "tokenID":1,
                "symbol":"EOS",
                "contract":"eosio.token",
                "precision":10000
            },
            {
                "symbol":"ADD",
                "contract":"eosadddddddd",
                "tokenID":2,
                "precision":10000
            }
        ]    
    }
}
```
### 2. Get token pair list on Findex
```javascript
GET /v1/pairList
```
#### Response(pairList contains multiple elements):
```json
{
    "code":200,
    "data":{
        "pairList":[
            {
                "pairID":1,
                "pair":"ADD/EOS",
                "quoteToken":"ADD",
                "quoteContract":"eosadddddddd",
                "baseToken":"EOS",
                "baseContract":"eosio.token"
            },
            {
                "pairID":2,
                "pair":"ATD/EOS",
                "quoteToken":"ATD",
                "quoteContract":"eosatidiumio",
                "baseToken":"EOS",
                "baseContract":"eosio.token"
            }
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

#### Response(The list may contains more elements if there are several pairs with the same name):
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
                    }
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
      "change":-0.0949,
      "pair_id":"14",
  }
}
```


### 5. Get token pair price on Findex using token contract and token name
```javascript
GET /v1/ticker
```
#### Parameters:
| Name        | Type |       Description                |
| ----------- | -----| ---------------------------------------------    |
| symbol      |STRING| {quoteContract}_{quoteTokenName}-{baseContract}_{baseTokenName} (eg:eosiomeetone_MEETONE-eosio.token_EOS) |

#### Response:
```json
{
  "code":200,
  "data": {
      "price":0.000055,
      "change":-0.0949,
      "pair_id":"9",
  }
}
```
