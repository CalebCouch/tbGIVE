# TBPUB

## Books & Pages
A TBPUB Documents consists of a single Book of Pages, Where a Book is a Json 
Array of Pages. Each Page must contain a price field, where the minimum price 
of a Page is one sat per byte.

## Publishing
To publish a Book, the hash of the Book is put in a bitcoin transaction that 
destroys at least as many sats as the sum of all its pages. To limit the number 
of Blockspace used, only the highest paying Book in a Block is concider valid.

## TBPUB Root Node

### Description
A TBPUB Root Node is a heavy-weight but fully trustless node capable of reading, 
verifying, and publishing books on the network.

When starting your Root Node, it will crawl through the blockchain, creating a 
list of all the published books, and other Root Nodes on the network. To obtain 
the data contained in the Books, you must be discoverable by the network to 
prevent spam. To be discoverable by other Root Nodes on the network, your Root 
Node will create a bitcoin transaction containing a did-dht key pointing to 
your Root Node. Each Root Node can only be read by another Root node once, 
Expecting that after obtaining and verifying the data, each will store it locally.

### Requirements
1. Bitcoin Core Full Node
2. Storage for published documents

## TBPUB Node

### Description
A TBPUB Node is a lightweight version of the Root Node that gets the blockchain 
from a trusted source such as blockstream.info. And obtains the published books 
from a non trusted source. After getting the list of published books and the 
blockchain data, It will verify that none of the books have been tampered with.

### Requirements
1. URL to a hosted and trusted service such as blockstream.info to get blockchain data
2. URL to a hosted and nontrusted service that gives the published books

## TBPUB Miner

### Description
A TBPUB Miner is an online service that runs a Root Node. It can allow others 
to publish data with a simple API and lighting payments. Or it can be a more 
lightweight option for App Providers to allow their Apps to read published Books.

## TBBandwidth

### Description
TBBandwidth is a built-in layer two protocol that allows for spamless discovery 
of DID-DHT keys. Additionally, by attaching a price to DID-DHT keys, other 
protocols can be built that only allow a certain number of interactions based 
on the cost of a did.
