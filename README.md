# TBPUB

## TBPUB Root Node

### Description

A TBPUB Root Node is a heavy-weight but fully trustless node capable of reading, verifying, 
and publishing documents on the network.

When starting your node it will crawl through the blockchain, creating a list of all 
the published documents, and  other Root Nodes on the network. 
To obtain the published data, you must first be on the network to prevent spam. 
Getting on the network requires that your Root Node is Discoverable via the Bitcoin blockchain. 
To allow your Root Node to be discovered, it will create a bitcoin transaction containing a 
did-dht key pointing to your Root Node. Each Root Node will only allow you to read the 
published data once. Every Root Node after verifying the documents, will store and allow 
other Root Nodes to read the data exactly once.

### Requirements
1. Bitcoin Core Full Node
2. Storage for published documents

## TBPUB Node

### Description

A TBPUB Node is a lightweight version of the Root Node that gets the blockchain from a trusted
source such as blockstream.info. And obtains the published documents from a non trusted source.

After getting the list of published documents and the blockchain data,
It will verify that none of the documents have been tampered with.

### Requirements
1. URL to a hosted and trusted service such as blockstream.info to get blockchain data
2. URL to a hosted and nontrusted service that gives the published documents

