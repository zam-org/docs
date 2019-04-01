# Terminology

The ZeroNet community have coined a number of words and phrases to describe different bits and pieces of ZeroNet. You can find a comprehensive list below.

Feel to free to append to this list by using the edit button.

### Zite

A "zite" is short for "ZeroNet website", and is mostly used as a differentiator between a website on the [clearnet](#clearnet) and a website on ZeroNet.

### Clearnet

The "clearnet" is what most people commonly refer to as the Internet. It is the publically-accessible list of websites that you can visit using your normal, unmodified web-browser. Clearnet sites do not require any special software to access outside of what is provided by your [operating system](https://en.wikipedia.org/wiki/Operating_system), but require a running server to operate and are prone to [censorship](https://en.wikipedia.org/wiki/Internet_censorship).

### Peer

A "peer", sometimes called a "node", is some computer connected to the ZeroNet network. Peers send and retrieve website data from each other.

### Peer-to-Peer

"Peer-to-Peer" is a [network topology](https://en.wikipedia.org/wiki/Network_topology) that consists of [peers](#Peer) that connect to one another. This is in contrast to a centralized topology which involves the use of single servers which many different nodes connect to. This topology is much easier to build, but requires the single server to require an ever-growing amount of resources to run, and puts those in charge of the central server in a position of power. Additionally, if the central server ever goes down, everybody is disconnected. In a peer-to-peer network, if one peer goes down other peers can continue to communicate amongst themselves.

### Tracker

A "tracker" is a server that ZeroNet uses to find the [IP addresses](https://en.wikipedia.org/wiki/IP_address) of other [peers](#Peer). When downloading a [zite's](#Zite) content, ZeroNet will ask the tracker which peers have data from the site it is looking for, and the tracker will return a limited, randomized list of addresses of peers that have that data. ZeroNet then directly contacts those peers and asks for specific files.

There are [plans](https://github.com/HelloZeroNet/ZeroNet/issues/57) to implement a [DHT](https://en.wikipedia.org/wiki/Distributed_hash_table) in ZeroNet which will reduce the need of trackers for the network to function.

### Merger

A "merger", or "merger zite", is a special type of [zite](#Zite) that shows information based on data stored in other zites, the latter being called "merged" zites. Mergers sites are typically programmed in a generic way, such that users can choose to mix and match different merged zites in order to affect what content is shown.

A good example and one of the first merger zites is [ZeroMe](https://zeronet.io/docs/using_zeronet/sample_sites/#zerome), which acts as a [peer-to-peer](#Peer-to-Peer) social network. A list of user IDs is stored on ZeroMe along with the address of their merged zite. If we want to view a user's profile and the posts they have made, we will need to download the merged site their information is stored on. Each merged zite has thousands on users on it, and people will naturally download the ones they need as they explore ZeroMe and view user profiles.

Merged zites are also very powerful as they allow multiple zites to share the same source of data. Thus you can have one merged zite, but multiple merger zites. Currently there do not seem to be any examples of this out in the wild, but doing so would be fairly trivial.