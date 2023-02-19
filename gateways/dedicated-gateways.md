# Dedicated Gateways

For those who need greater speed or increased rate limits when retrieving content, Pinata lets users on any of our paid plans create dedicated gateways.

What are the benefits of a dedicated gateway?

* Unmatched speed through our over 200 edge caching locations around the world
* No rate limits for requesting content

To get started, [you'll need to sign up for a paid plan](https://pinata.cloud/billing). From there, you can go to our [Gateways page to create your first gateway](https://pinata.cloud/gateway).

## Getting Started

On the Gateway Page, simply click Create Gateway:

You'll be prompted to create your gateway through an easy-to-use wizard. Provide a name for your gateway then choose whether your gateway is open or restricted.

## Open vs. Restricted

What's the difference between an open gateway and a restricted gateway? In both cases, the content served by the gateway will be available to anyone with the link. However, the restricted gateway will only serve content that is pinned on your account.

An open gateway will (assuming it can find the content on the IPFS network) serve up any content even if it's not pinned to your account. This is great for wide accessibility but can lead to higher usage costs. Restricted gateways mean that you're only charged for delivering your content.

To change a gateway from restricted to open, you would need to use the [gateway-access-controls.md](gateway-access-controls.md "mention"), by adding either an Access Token, Host Origin, or IP Address. When you add one of these access controls, the gateway will be able to fetch content outside your account as the restriction requirement is met.

## What is Bandwidth?

Bandwidth is the data that represents the item you or your users are viewing through your dedicated gateway. Each image, video, audio, and any other type of file that is displayed through the gateway or downloaded through the gateway is made of up data. That data is sent from an IPFS node to your computer. The size of this data is bandwidth.

You can track your bandwidth for any gateway you have set up by going to your Gateways page and clicking on the subdomain link for your gateway.

## How Do I Use My Gateway

To view content through your gateway, grab the CID of the file you'd like to view and add it to your gateway URL like this:

`https://<Your Gateway Subdomain>.mypinata.cloud/ipfs/<Your CID>`

Simple as that!

## How do I convert other gateway URLs to use my gateway?

In many cases, projects will directly put an entire gateway URL on-chain (such as when minting NFTs).

If you find yourself reading from a location that may provide a gateway URL, Pinata created the [ipfs-gateway-tools](https://github.com/PinataCloud/ipfs-gateway-tools) toolkit to help you out.

This toolkit can easily convert any standard IPFS gateway URL, as well as URIs with the `ipfs://<CID>` format to a URL that utilizes your gateway.

## Adding a Custom Domain

Pinata also allows you to create a custom domain for your dedicated gateway. Simply click the menu button on the right side of your gateway row in the table on the Gateways page, then click Add Custom Domain. You'll need to own the domain you want to use. When you enter your domain, you will be prompted to enter DNS information through your registrar.

## We want your feedback!

Have a suggestion? Have a complaint? Confused about something in the documentation? Just want to say hi?

We want to make Pinata the best product available. That involves listening to our users and addressing their needs.

Send us an email at [team@pinata.cloud](mailto:team@pinata.cloud) and we'll see how we can help.
