# TBPUB

## Abstract

tbPUB is a peer to peer network whick uses the bitcoin core network for 
discovery of nodes and to store the hashes of published documents. 
tbPUB prevents spam by requiring a small amount of BTC to be destroyed 
before allowing a document to be published.

### Publication

A publication takes a set of data and creates a bitcoin UTXO that 
contains the HASH of the data. The data is then read and replicated 
by all other tbPUB nodes in order to ensure its always avalible.

### Hosting

A secondary use of the tbPUB nodes is a hosting of certian types of data
at certian routes on the node. Spam is prevented by requring a certian 
amount of BTC to be destroyed to allow your node to be discoverd by the 
network.

## Terms
| Name | Description |
|------|-------------|
| DID | Decentralized-Identity |
| DID-DHT-Key | A key pointing to a DID in the DHT protocal |
| HASH | A sha-160 20 byte hash |
| COST | The amount of BTC destroyed by sending it to a script starting with OP_RETURN |
| ROUTE | A string pointing to a set of data in tbpub with attached consensus rules |

## Routes
| Name | Description | Consensus |
|------|-------------|-----------|
| / | Default route is reserved for server messages of no particular format | 1 sat per byte |
| /HASH | Any 20 character string is reserved as a route that references the data hosted | 1 sat per byte |

## CLI
| Name | Arguments | Description |
|------|-----------|-------------|
| get-dids | None | Returns a Json Array of all discovered DID-DHT keys |
| get | route, did-dht-key | Returns data from a given route, If no did-dht-key is specified return a Json Array of the data from all discovered DIDs at that route |
| publish-did | did-dht-key, price | Creates and broadcasts a bitcoin transaction containing the did-dht-key with the given price. Price must be at least 1000 sats |
| publish-dids | [did-dht-key, price] | Publishes all dids in the given array in a single bitcoin transaction, Price must be at least 1000 sats per did |
| publish-data | filename, price | Creatse and broadcasts a bitcoin transaction containing the hash of the data found in the given file, Ensuring the price is greater then the number of bytes |

## Dependencies
All dependencies are pre-packaged in the binaries found in the releases section.

| Name | Version | Description |
|------|---------|-------------|
| Bitcoin Core | ? | Used to locate or publish did-dht-keys and data hash's on the Blockchain |
| DID-DHT | ? | Used to discover or publish dids on the mainline DHT protocol |
