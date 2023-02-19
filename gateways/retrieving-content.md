# Retrieving Content

All of Pinata's content is avalable on the public IPFS network. This means that anybody running an IPFS node can access content stored on Pinata through their own IPFS node.

However, directly running a node isn't the only way to access content, nor is it the easiest. The most common way to retrieve content on the IPFS network is through an IPFS gateway.

IPFS gateways are IPFS nodes that provide access to the IPFS network through a web URL that often takes the following form: [https://example.gateway.com/ipfs/CID](https://example.gateway.com/ipfs/CID), where the `CID` is the content identifier (also known as a hash) for the content you want to retrieve.

### **The Pinata Public Gateway**

Pinata provides a public gateway for users who are just getting started at [https://gateway.pinata.cloud](https://gateway.pinata.cloud).

An example of accessing content from this gateway can be seen with: `https://gateway.pinata.cloud/ipfs/bafybeifx7yeb55armcsxwwitkymga5xf53dxiarykms3ygqic223w5sk3m`

**The Public Gateway should not be used in production. It is designed for testing, is not designed for speed, and is heavily rate limited.**

### **Dedicated Gateways**

For those who need greater speed or increased rate limits when retrieving content, Pinata lets users on our professional plan create dedicated gateways.

What are the benefits of a dedicated gateway?

* Unmatched speed through our over 200 edge caching locations around the world
* No rate limits for requesting content

To get started, [you'll need to sign up for the Professional Plan](https://pinata.cloud/billing). From there, you can go to our [Gateways page to create your first gateway](https://pinata.cloud/gateway).

You can also read additional documentation on how to set up a dedicated gateway [here](dedicated-gateways.md).

## We want your feedback!

Have a suggestion? Have a complaint? Confused about something in the documentation? Just want to say hi?

We want to make Pinata the best product available. That involves listening to our users and addressing their needs.

Send us an email at [team@pinata.cloud](mailto:team@pinata.cloud) and we'll see how we can help.
