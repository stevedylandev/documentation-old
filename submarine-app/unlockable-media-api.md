---
description: ℹ️ This endpoint is in beta and is subject to change
---

# Unlockable Media API

This API endpoint will allow you to programmatically create unlockable pages for the Submarine app. These pages are normally done through the non-technical interface, but this endpoint would allow you to create them faster and at scale. The functionality is still under beta and will be altered as time goes on.&#x20;

{% swagger method="post" path="/metadata" baseUrl="https://app.submarine.my/api" summary="Creates Unlockable Content Page in Submarine.me" expanded="true" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Bearer PINATA_JWT
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" required="true" %}
A string representing the name that will be displayed on the unlock page
{% endswagger-parameter %}

{% swagger-parameter in="body" name="description" required="true" %}
A short description of the unlockable content and anything else you'd like to include
{% endswagger-parameter %}

{% swagger-parameter in="body" name="thumbnail" type="string" %}
An IPFS CID of an image that can be used as the thumbnail that represents your media
{% endswagger-parameter %}

{% swagger-parameter in="body" name="submarineCid" required="true" %}
The CID of the uploaded submarine content you want to be unlocked This can be done through the Submarine API or Pinata App
{% endswagger-parameter %}

{% swagger-parameter in="body" name="unlockInfo" required="true" type="string" %}
Object of the unlock info for the page (see below for more info)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="customizations" %}
Object of optional pieces of the page you can customize (see below for more info)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="shortId" required="true" %}
This is a unique identifier for the unlock page. It can be any combination of letters and numbers as long as it is valid in a URL and unique in our database
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "status": 200,
  "totalItems": 0,
  "items": [
    {
      "id": "string",
      "createdAt": "2022-05-20T20:01:26.679Z",
      "cid": "string",
      "name": "string",
      "mimeType": "string",
      "originalname": "string",
      "size": 0,
      "metadata": {},
      "pinToIPFS": false,
      "isDuplicate": false
    }
  ]
}
```
{% endswagger-response %}
{% endswagger %}

Details for `unlockInfo` object:

* `type`: How the media will be unlocked. Available options are: `nft`, `retweet`, `location,` and `twitch`
* `contract`: For Ethereum or EVM compatible NFTs, this is the smart contract address for the NFT collection
* `network`: The network associated with the blockchain you’ve chosen. Available options are: `Mainnet`, `Goerli`, `Mumbai`, `Fuji`, `Mainnet-Beta`, `Devnet.`
* `blockchain`: This is the blockchain the NFT lives on. Available options are: Ethereum, Polygon, Avalanche, Solana
* `updateAuthority`: This is a Solana-specific field representing the address that can update the NFT program.
* `mintAddress`: This is a Solana-specific field representing the address that minted the NFT.
* `tokenId`: This is an EVM-chain (Ethereum, Polygon, Avalanche) specific field that will only allow media to be unlocked if you own the specific tokenId in question. Note: this is required for ERC1155 NFTs.
* `tweetUrl`: This is the full URL to a tweet that needs to be retweeted if using the Retweet to Unlock functionality
* `lat`: This is the latitudinal coordinates required to unlock geolocation-gated media.
* `long`: This is the longitudinal coordinates required to unlock geolocation-gated media.
* `distance`: This is how far (in miles) someone can be from the lat/long coordinates when trying to unlock geolocation-gated media.
* `loginName`: This is the username that must be subscribed to when using the Twitch unlock

Details for `customizations` object:

* `backgroundCid`: This is the IPFS CID for a background image to use when customizing your unlock page.
* `buttonColor`:&#x20;
  * `hex`: This is the full hex color for the buttons that will appear on the unlock page
* `buttonTextColor`:&#x20;
  * `hex`: This is the full hex color for the text that will appear on all buttons on the unlock page
* `buttonShape`: This is a string referencing the shape of the buttons on the unlock page. Available options are: `rounded`, `square`
* `fontFamily`: This is a string representation of the font family to use on the unlock page. Available options are: `Inter`, `Lato`, `Open Sans`, `Roboto`, `Roboto Condensed`, `Source Sans Pro`
* `logoCid`: This is the IPFS CID representing the logo you want to use in the top-left of the unlock page.&#x20;

{% tabs %}
{% tab title="cURL" %}
```bash
curl --location --request POST 'https://app.submarine.me/api/metadata' \
--header 'Authorization: Bearer PINATA_JWT' \
--header 'Content-Type: application/json' \
--data-raw '{
   "name": "Test API Request",
   "description": "This is a test through the API",
   "thumbnail": "Qmbuv4mjjMKaSFVgLNesi9VFxjfaeGzhZ9r51w2ntGMFCk",
   "submarineCid": "bafkreidevytzhkzmwjyzdijipawftj5bmsdsh7m6if7e536wasnzybuoe4",
   "unlockInfo": {
       "type": "nft",
       "contract": "0x089045a72b70b05ec22ea4be23ebc07768fb3e7f",
       "network": "Mainnet",
       "blockchain": "Ethereum"
   },
   "customizations": {
       "backgroundCid": "QmQvCXbbWJ1yGrRzQWSvo8Vbu1C98QMEoLeQJdM4EtHYpx",
       "buttonColor": {
           "hex": "#fccf03"
       },
       "buttonTextColor": {
           "hex": "#ffffff"
       },
       "buttonShape": "square",
       "fontFamily": "Lato",
       "logoCid": ""
   },
   "shortId": "PPBqW29i"
}

```
{% endtab %}

{% tab title="Node JS" %}
```javascript
var axios = require('axios');
var data = JSON.stringify({
  "name": "Test API Request",
  "description": "This is a test through the API",
  "thumbnail": "Qmbuv4mjjMKaSFVgLNesi9VFxjfaeGzhZ9r51w2ntGMFCk",
  "submarineCid": "bafkreidevytzhkzmwjyzdijipawftj5bmsdsh7m6if7e536wasnzybuoe4",
  "unlockInfo": {
    "type": "nft",
    "contract": "0x089045a72b70b05ec22ea4be23ebc07768fb3e7f",
    "network": "Mainnet",
    "blockchain": "Ethereum"
  },
  "customizations": {
    "backgroundCid": "QmQvCXbbWJ1yGrRzQWSvo8Vbu1C98QMEoLeQJdM4EtHYpx",
    "buttonColor": {
      "hex": "#fccf03"
    },
    "buttonTextColor": {
      "hex": "#ffffff"
    },
    "buttonShape": "square",
    "fontFamily": "Lato",
    "logoCid": ""
  },
  "shortId": "PPBqW29i"
});

var config = {
  method: 'post',
maxBodyLength: Infinity,
  url: 'https://app.submarine.me/api/metadata',
  headers: { 
    'Authorization': 'Bearer PINATA_JWT', 
    'Content-Type': 'application/json'
  },
  data : data
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});

```
{% endtab %}

{% tab title="Python" %}
```python
import requests
import json

url = "https://app.submarine.me/api/metadata"

payload = json.dumps({
  "name": "Test API Request",
  "description": "This is a test through the API",
  "thumbnail": "Qmbuv4mjjMKaSFVgLNesi9VFxjfaeGzhZ9r51w2ntGMFCk",
  "submarineCid": "bafkreidevytzhkzmwjyzdijipawftj5bmsdsh7m6if7e536wasnzybuoe4",
  "unlockInfo": {
    "type": "nft",
    "contract": "0x089045a72b70b05ec22ea4be23ebc07768fb3e7f",
    "network": "Mainnet",
    "blockchain": "Ethereum"
  },
  "customizations": {
    "backgroundCid": "QmQvCXbbWJ1yGrRzQWSvo8Vbu1C98QMEoLeQJdM4EtHYpx",
    "buttonColor": {
      "hex": "#fccf03"
    },
    "buttonTextColor": {
      "hex": "#ffffff"
    },
    "buttonShape": "square",
    "fontFamily": "Lato",
    "logoCid": ""
  },
  "shortId": "PPBqW29i"
})
headers = {
  'Authorization': 'Bearer PINATA_JWT',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
pyu
```
{% endtab %}

{% tab title="Go" %}
```go
package main

import (
  "fmt"
  "strings"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://app.submarine.me/api/metadata"
  method := "POST"

  payload := strings.NewReader(`{
   "name": "Test API Request",
   "description": "This is a test through the API",
   "thumbnail": "Qmbuv4mjjMKaSFVgLNesi9VFxjfaeGzhZ9r51w2ntGMFCk",
   "submarineCid": "bafkreidevytzhkzmwjyzdijipawftj5bmsdsh7m6if7e536wasnzybuoe4",
   "unlockInfo": {
       "type": "nft",
       "contract": "0x089045a72b70b05ec22ea4be23ebc07768fb3e7f",
       "network": "Mainnet",
       "blockchain": "Ethereum"
   },
   "customizations": {
       "backgroundCid": "QmQvCXbbWJ1yGrRzQWSvo8Vbu1C98QMEoLeQJdM4EtHYpx",
       "buttonColor": {
           "hex": "#fccf03"
       },
       "buttonTextColor": {
           "hex": "#ffffff"
       },
       "buttonShape": "square",
       "fontFamily": "Lato",
       "logoCid": ""
   },
   "shortId": "PPBqW29i"
}
`)

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("Authorization", "Bearer PINATA_JWT")
  req.Header.Add("Content-Type", "application/json")

  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```
{% endtab %}
{% endtabs %}

