# IPFS Pinning

In IPFS, nodes frequently cache content that gets routed through them. A node is a program that connects you to IPFS and stores files. This means that popular content frequently lives on many places of the network at once.

However, eventually, the node cache becomes full, and then **garbage collection** happens. This means that the node empties its cache to make room for more content.

When this happens, all content that isn't "pinned" gets deleted.

#### **What does it mean to 'pin' a file?**

When you "pin" date on an IPFS node, it ensures that the content will always be available, as long as the node is connected to the IPFS network.

Pinning prevents important data from being deleted from your node. You and only you can control and pin data on your node(s)—you can not force other nodes on the IPFS network to pin your content for you. So, to guarantee your content stays pinned, you have to run your own IPFS nodes.

Once your file is pinned to IPFS, you have full control to share, distribute, monetize and share your files however you’d like.

\[\[ Further reading:[ What is an IPFS Pinning Service ](https://medium.com/pinata/what-is-an-ipfs-pinning-service-f6ed4cd7e475)]]
