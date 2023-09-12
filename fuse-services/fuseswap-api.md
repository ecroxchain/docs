---
description: FuseSwap API is an auxiliary service to ease the integration with FuseSwap DEX
---

# Fuseswap API

## Fuseswap Backend API v0.1.0

The Fuseswap Backend REST API is used for generating trading data for frontend clients

## PriceChange

### Get price change for token over last 24 hours

[Back to top](https://github.com/fuseio/fuseswap-service/blob/master/docs/api.md#top)

```text
GET /pricechange
```

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| tokenAddress | `String` | The currency address |

#### Success Response

Success-Response:

```text

{
    "data": {
        "priceChange": "4.761727644165598",
        "currentPrice": "3760.8426158182515",
        "previousPrice": "3589.901293526158"
    }
}
```

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| priceChange | `String` | The price change ratio of the token |
| currentPrice | `String` | The current price of the token |
| previousPrice | `String` | The previous price of the token |

### Get price change for token over time duration

[Back to top](https://github.com/fuseio/fuseswap-service/blob/master/docs/api.md#top)

```text
POST /pricechange
```

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| tokenAddress | `String` | The currency address |
| duration | `Object` | The duration object to calculate the price change over the timeframe duration should be passed as an object according to [https://day.js.org/docs/en/durations/creating](https://day.js.org/docs/en/durations/creating) for example duration of {days: 1} means a duration of one day |

#### Success Response

Success-Response:

```text

{
    "data": {
        "priceChange": "4.761727644165598",
        "currentPrice": "3760.8426158182515",
        "previousPrice": "3589.901293526158"
    }
}
```

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| priceChange | `String` | The price change ratio of the token |
| currentPrice | `String` | The current price of the token |
| previousPrice | `Object` | The previous price of the token |

## Price

### Get latest price for a token

[Back to top](https://github.com/fuseio/fuseswap-service/blob/master/docs/api.md#top)

```text
GET /price
```

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| tokenAddress | `String` | The currency address |

#### Success Response

Success-Response:

```text

{
 "data": {
     "price":1.009884197756788
  }
}
```

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| price | `Number` | The price of the token |

## Stats

### Get historical statistics of the token

[Back to top](https://github.com/fuseio/fuseswap-service/blob/master/docs/api.md#top)

```text
GET /stats/:tokenAddress?=limit={limit}
```

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| tokenAddress | `String` | The currency address |
| limit | `String` | The number of days to return statistics for \(query param\) |

#### Success Response

Success-Response:

```text

{
 "data": [
      {
          "address": "0xa722c13135930332eb3d749b2f0906559d2c5b99",
          "price": "2389.74779405372110747871079158035",
          "volume": "3343.67560523501352604818272285103",
          "timestamp": 1619395200,
          "date": "2021-04-26T00:00:00.000Z"
      }
]
```

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| array | `Object[]` | of token stats objects, see example below |

## Swap

### Create a quote for a token pair

[Back to top](https://github.com/fuseio/fuseswap-service/blob/master/docs/api.md#top)

```text
POST /swap/quote
```

#### Parameter Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| currencyIn | `String` | The currency to spend |
| currencyOut | `String` | The desired currency out address |
| inputAmount | `String` | The desired amount to spend |

#### Success Response

Success-Response:

```text

{
    "data": {
        "info": {
            "inputAmount": "1",
            "outputAmount": "965.616",
            "route": [
                "WETH",
                "USDC"
            ],
            "inputToken": "WETH",
            "outputToken": "USDC",
            "executionPrice": "965.617",
            "nextMidPrice": "722.082",
            "priceImpact": "25.612"
        },
        "trade": {
            "route": {
                "pairs": [
                    {
                        "liquidityToken": {
                            "decimals": 18,
                            "symbol": "UNI-V2",
                            "name": "Uniswap V2",
                            "chainId": 988207,
                            "address": "0x20a680D69a5aE2677B8CF43aBF63aAD6D8d5119A"
                        },
                        "tokenAmounts": [
                            {
                                "numerator": [
                                    -491531807
                                ],
                                "denominator": [
                                    1000000
                                ],
                                "currency": {
                                    "decimals": 6,
                                    "symbol": "USDC",
                                    "name": "USD Coin on Ecrox",
                                    "chainId": 988207,
                                    "address": "0x620fd5fa44BE6af63715Ef4E65DDFA0387aD13F5",
                                    "tokenInfo": {
                                        "name": "USD Coin on Ecrox",
                                        "address": "0x620fd5fa44BE6af63715Ef4E65DDFA0387aD13F5",
                                        "symbol": "USDC",
                                        "decimals": 6,
                                        "chainId": 988207,
                                        "logoURI": "https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/assets/0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48/logo.png"
                                    },
                                    "tags": []
                                },
                                "token": {
                                    "decimals": 6,
                                    "symbol": "USDC",
                                    "name": "USD Coin on Ecrox",
                                    "chainId": 988207,
                                    "address": "0x620fd5fa44BE6af63715Ef4E65DDFA0387aD13F5",
                                    "tokenInfo": {
                                        "name": "USD Coin on Ecrox",
                                        "address": "0x620fd5fa44BE6af63715Ef4E65DDFA0387aD13F5",
                                        "symbol": "USDC",
                                        "decimals": 6,
                                        "chainId": 988207,
                                        "logoURI": "https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/assets/0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48/logo.png"
                                    },
                                    "tags": []
                                }
                            },
                            {
                                "numerator": [
                                    -2070596893,
                                    682205361
                                ],
                                "denominator": [
                                    -1486618624,
                                    232830643
                                ],
                                "currency": {
                                    "decimals": 18,
                                    "symbol": "WETH",
                                    "name": "Wrapped Ether on Ecrox",
                                    "chainId": 988207,
                                    "address": "0xd8Bf72f3e163B9CF0C73dFdCC316417A5ac20670",
                                    "tokenInfo": {
                                        "name": "Wrapped Ether on Ecrox",
                                        "address": "0xd8Bf72f3e163B9CF0C73dFdCC316417A5ac20670",
                                        "symbol": "WETH",
                                        "decimals": 18,
                                        "chainId": 988207,
                                        "logoURI": "https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/assets/0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2/logo.png"
                                    },
                                    "tags": []
                                },
                                "token": {
                                    "decimals": 18,
                                    "symbol": "WETH",
                                    "name": "Wrapped Ether on Ecrox",
                                    "chainId": 988207,
                                    "address": "0xd8Bf72f3e163B9CF0C73dFdCC316417A5ac20670",
                                    "tokenInfo": {
                                        "name": "Wrapped Ether on Ecrox",
                                        "address": "0xd8Bf72f3e163B9CF0C73dFdCC316417A5ac20670",
                                        "symbol": "WETH",
                                        "decimals": 18,
                                        "chainId": 988207,
                                        "logoURI": "https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/assets/0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2/logo.png"
                                    },
                                    "tags": []
                                }
                            }
                        ]
                    }
                ],
                "path": [
                    {
                        "decimals": 18,
                        "symbol": "WETH",
                        "name": "Wrapped Ether on Ecrox",
                        "chainId": 988207,
                        "address": "0xd8Bf72f3e163B9CF0C73dFdCC316417A5ac20670",
                        "tokenInfo": {
                            "name": "Wrapped Ether on Ecrox",
                            "address": "0xd8Bf72f3e163B9CF0C73dFdCC316417A5ac20670",
                            "symbol": "WETH",
                            "decimals": 18,
                            "chainId": 988207,
                            "logoURI": "https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/assets/0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2/logo.png"
                        },
                        "tags": []
                    },
                    {
                        "decimals": 6,
                        "symbol": "USDC",
                        "name": "USD Coin on Ecrox",
                        "chainId": 988207,
                        "address": "0x620fd5fa44BE6af63715Ef4E65DDFA0387aD13F5",
                        "tokenInfo": {
                            "name": "USD Coin on Ecrox",
                            "address": "0x620fd5fa44BE6af63715Ef4E65DDFA0387aD13F5",
                            "symbol": "USDC",
                            "decimals": 6,
                            "chainId": 988207,
                            "logoURI": "https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/assets/0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48/logo.png"
                        },
                        "tags": []
                    }
                ],
                "midPrice": {
                    "numerator": [
                        -491531807
                    ],
                    "denominator": [
                        -2070596893,
                        682205361
                    ],
                    "baseCurrency": {
                        "decimals": 18,
                        "symbol": "WETH",
                        "name": "Wrapped Ether on Ecrox",
                        "chainId": 988207,
                        "address": "0xd8Bf72f3e163B9CF0C73dFdCC316417A5ac20670",
                        "tokenInfo": {
                            "name": "Wrapped Ether on Ecrox",
                            "address": "0xd8Bf72f3e163B9CF0C73dFdCC316417A5ac20670",
                            "symbol": "WETH",
                            "decimals": 18,
                            "chainId": 988207,
                            "logoURI": "https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/assets/0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2/logo.png"
                        },
                        "tags": []
                    },
                    "quoteCurrency": {
                        "decimals": 6,
                        "symbol": "USDC",
                        "name": "USD Coin on Ecrox",
                        "chainId": 988207,
                        "address": "0x620fd5fa44BE6af63715Ef4E65DDFA0387aD13F5",
                        "tokenInfo": {
                            "name": "USD Coin on Ecrox",
                            "address": "0x620fd5fa44BE6af63715Ef4E65DDFA0387aD13F5",
                            "symbol": "USDC",
                            "decimals": 6,
                            "chainId": 988207,
                            "logoURI": "https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/assets/0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48/logo.png"
                        },
                        "tags": []
                    },
                    "scalar": {
                        "numerator": [
                            -1486618624,
                            232830643
                        ],
                        "denominator": [
                            1000000
                        ]
                    }
                },
                "input": {
                    "decimals": 18,
                    "symbol": "WETH",
                    "name": "Wrapped Ether on Ecrox",
                    "chainId": 988207,
                    "address": "0xd8Bf72f3e163B9CF0C73dFdCC316417A5ac20670",
                    "tokenInfo": {
                        "name": "Wrapped Ether on Ecrox",
                        "address": "0xd8Bf72f3e163B9CF0C73dFdCC316417A5ac20670",
                        "symbol": "WETH",
                        "decimals": 18,
                        "chainId": 988207,
                        "logoURI": "https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/assets/0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2/logo.png"
                    },
                    "tags": []
                },
                "output": {
                    "decimals": 6,
                    "symbol": "USDC",
                    "name": "USD Coin on Ecrox",
                    "chainId": 988207,
                    "address": "0x620fd5fa44BE6af63715Ef4E65DDFA0387aD13F5",
                    "tokenInfo": {
                        "name": "USD Coin on Ecrox",
                        "address": "0x620fd5fa44BE6af63715Ef4E65DDFA0387aD13F5",
                        "symbol": "USDC",
                        "decimals": 6,
                        "chainId": 988207,
                        "logoURI": "https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/assets/0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48/logo.png"
                    },
                    "tags": []
                }
            },
            "tradeType": 0,
            "inputAmount": {
                "numerator": [
                    -1486618624,
                    232830643
                ],
                "denominator": [
                    -1486618624,
                    232830643
                ],
                "currency": {
                    "decimals": 18,
                    "symbol": "WETH",
                    "name": "Wrapped Ether on Ecrox",
                    "chainId": 988207,
                    "address": "0xd8Bf72f3e163B9CF0C73dFdCC316417A5ac20670",
                    "tokenInfo": {
                        "name": "Wrapped Ether on Ecrox",
                        "address": "0xd8Bf72f3e163B9CF0C73dFdCC316417A5ac20670",
                        "symbol": "WETH",
                        "decimals": 18,
                        "chainId": 988207,
                        "logoURI": "https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/assets/0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2/logo.png"
                    },
                    "tags": []
                },
                "token": {
                    "decimals": 18,
                    "symbol": "WETH",
                    "name": "Wrapped Ether on Ecrox",
                    "chainId": 988207,
                    "address": "0xd8Bf72f3e163B9CF0C73dFdCC316417A5ac20670",
                    "tokenInfo": {
                        "name": "Wrapped Ether on Ecrox",
                        "address": "0xd8Bf72f3e163B9CF0C73dFdCC316417A5ac20670",
                        "symbol": "WETH",
                        "decimals": 18,
                        "chainId": 988207,
                        "logoURI": "https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/assets/0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2/logo.png"
                    },
                    "tags": []
                }
            },
            "outputAmount": {
                "numerator": [
                    965616800
                ],
                "denominator": [
                    1000000
                ],
                "currency": {
                    "decimals": 6,
                    "symbol": "USDC",
                    "name": "USD Coin on Ecrox",
                    "chainId": 988207,
                    "address": "0x620fd5fa44BE6af63715Ef4E65DDFA0387aD13F5",
                    "tokenInfo": {
                        "name": "USD Coin on Ecrox",
                        "address": "0x620fd5fa44BE6af63715Ef4E65DDFA0387aD13F5",
                        "symbol": "USDC",
                        "decimals": 6,
                        "chainId": 988207,
                        "logoURI": "https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/assets/0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48/logo.png"
                    },
                    "tags": []
                },
                "token": {
                    "decimals": 6,
                    "symbol": "USDC",
                    "name": "USD Coin on Ecrox",
                    "chainId": 988207,
                    "address": "0x620fd5fa44BE6af63715Ef4E65DDFA0387aD13F5",
                    "tokenInfo": {
                        "name": "USD Coin on Ecrox",
                        "address": "0x620fd5fa44BE6af63715Ef4E65DDFA0387aD13F5",
                        "symbol": "USDC",
                        "decimals": 6,
                        "chainId": 988207,
                        "logoURI": "https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/assets/0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48/logo.png"
                    },
                    "tags": []
                }
            },
            "executionPrice": {
                "numerator": [
                    965616800
                ],
                "denominator": [
                    -1486618624,
                    232830643
                ],
                "baseCurrency": {
                    "decimals": 18,
                    "symbol": "WETH",
                    "name": "Wrapped Ether on Ecrox",
                    "chainId": 988207,
                    "address": "0xd8Bf72f3e163B9CF0C73dFdCC316417A5ac20670",
                    "tokenInfo": {
                        "name": "Wrapped Ether on Ecrox",
                        "address": "0xd8Bf72f3e163B9CF0C73dFdCC316417A5ac20670",
                        "symbol": "WETH",
                        "decimals": 18,
                        "chainId": 988207,
                        "logoURI": "https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/assets/0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2/logo.png"
                    },
                    "tags": []
                },
                "quoteCurrency": {
                    "decimals": 6,
                    "symbol": "USDC",
                    "name": "USD Coin on Ecrox",
                    "chainId": 988207,
                    "address": "0x620fd5fa44BE6af63715Ef4E65DDFA0387aD13F5",
                    "tokenInfo": {
                        "name": "USD Coin on Ecrox",
                        "address": "0x620fd5fa44BE6af63715Ef4E65DDFA0387aD13F5",
                        "symbol": "USDC",
                        "decimals": 6,
                        "chainId": 988207,
                        "logoURI": "https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/assets/0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48/logo.png"
                    },
                    "tags": []
                },
                "scalar": {
                    "numerator": [
                        -1486618624,
                        232830643
                    ],
                    "denominator": [
                        1000000
                    ]
                }
            },
            "nextMidPrice": {
                "numerator": [
                    -1457148607
                ],
                "denominator": [
                    737751779,
                    915036005
                ],
                "baseCurrency": {
                    "decimals": 18,
                    "symbol": "WETH",
                    "name": "Wrapped Ether on Ecrox",
                    "chainId": 988207,
                    "address": "0xd8Bf72f3e163B9CF0C73dFdCC316417A5ac20670",
                    "tokenInfo": {
                        "name": "Wrapped Ether on Ecrox",
                        "address": "0xd8Bf72f3e163B9CF0C73dFdCC316417A5ac20670",
                        "symbol": "WETH",
                        "decimals": 18,
                        "chainId": 988207,
                        "logoURI": "https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/assets/0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2/logo.png"
                    },
                    "tags": []
                },
                "quoteCurrency": {
                    "decimals": 6,
                    "symbol": "USDC",
                    "name": "USD Coin on Ecrox",
                    "chainId": 988207,
                    "address": "0x620fd5fa44BE6af63715Ef4E65DDFA0387aD13F5",
                    "tokenInfo": {
                        "name": "USD Coin on Ecrox",
                        "address": "0x620fd5fa44BE6af63715Ef4E65DDFA0387aD13F5",
                        "symbol": "USDC",
                        "decimals": 6,
                        "chainId": 988207,
                        "logoURI": "https://raw.githubusercontent.com/trustwallet/assets/master/blockchains/ethereum/assets/0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48/logo.png"
                    },
                    "tags": []
                },
                "scalar": {
                    "numerator": [
                        -1486618624,
                        232830643
                    ],
                    "denominator": [
                        1000000
                    ]
                }
            },
            "priceImpact": {
                "numerator": [
                    856059488,
                    1380480455,
                    -336661329,
                    549156708,
                    8387887
                ],
                "denominator": [
                    1479278592,
                    1664736159,
                    977444823,
                    944423004,
                    32750022
                ]
            }
        }
    }
}
```

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| info | `Object` | Simplied quote object containing information about the trade |
| trade | `Object` | The trade object containing information about the [trade](https://uniswap.org/docs/v2/SDK/trade) e.g price |

### Create swap parameters for a Trade

[Back to top](https://github.com/fuseio/fuseswap-service/blob/master/docs/api.md#top)

```text
POST /swap/swapcallparameters
```

#### Parameter Parameters

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">currencyIn</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">The currency to spend</td>
    </tr>
    <tr>
      <td style="text-align:left">currencyOut</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">The desired currency out address</td>
    </tr>
    <tr>
      <td style="text-align:left">inputAmount</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left">The desired amount to spend</td>
    </tr>
    <tr>
      <td style="text-align:left">recipient</td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">The address that should receive the output of the swap</td>
    </tr>
    <tr>
      <td style="text-align:left">allowedSlippage</td>
      <td style="text-align:left"><code>Number</code>
      </td>
      <td style="text-align:left">
        <p><b>optional</b>
        </p>
        <p>How much the execution price is allowed to move unfavorably from the trade
          execution price in Basis Points(BIPS)<em>Default value: 50</em>
          <br />
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">ttl</td>
      <td style="text-align:left"><code>Number</code>
      </td>
      <td style="text-align:left">
        <p><b>optional</b>
        </p>
        <p>How long the swap is valid until it expires in seconds<em>Default value: 1200</em>
          <br
          />
        </p>
      </td>
    </tr>
  </tbody>
</table>

#### Success Response

Success-Response:

```text
{
     "methodName": "swapExactETHForTokens",
     "args": [
         "0x8f1573df661b2f",
         [
             "0x0BE9e53fd7EDaC9F859882AfdDa116645287C629",
             "0xFaDbBF8Ce7D5b7041bE672561bbA99f79c532e10",
             "0x94Ba7A27c7A95863d1bdC7645AC2951E0cca06bA"
         ],
         "0x5670d7076E7b3604ceb07c003ff0920490756587",
         "0x5fdf7e43"
     ],
     "value": "0xde0b6b3a7640000",
     "rawTxn": {
         "data": "0x7ff36ab5000000000000000000000000000000000000000000000000008f1573df661b2f00000000000000000000000000000000000000000000000000000000000000800000000000000000000000005670d7076e7b3604ceb07c003ff0920490756587000000000000000000000000000000000000000000000000000000005fdf7e4300000000000000000000000000000000000000000000000000000000000000030000000000000000000000000be9e53fd7edac9f859882afdda116645287c629000000000000000000000000fadbbf8ce7d5b7041be672561bba99f79c532e1000000000000000000000000094ba7a27c7a95863d1bdc7645ac2951e0cca06ba",
         "to": "0xFB76e9E7d88E308aB530330eD90e84a952570319",
         "value": {
             "type": "BigNumber",
             "hex": "0x0de0b6b3a7640000"
         }
     }
}
```

#### Success 200

| Name | Type | Description |
| :--- | :--- | :--- |
| methodName | `String` | The method to call on Fuseswap RouterV2 |
| args | `String[]` | The arguments to pass to the method, all hex encoded |
| value | `String` | The amount of wei to send in hex |
| rawTxn | `Object` | Unsigned transaction which represents the transaction that needs to be signed and submitted to the network |

