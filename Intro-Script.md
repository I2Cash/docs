# Intro script

This will be the script for an easy to undestand introduction to I2Cash. The script can be used for both an explainer video as well as an infographic.

The idea is to tell a story that makes sense for people. The video/infographic should obviously be correct, but any unnessesary details should be omitted.

## 1. Intro.
I2Cash is not built upon blockchains or lists of transactions like traditional cryptocurrencies. It is a new system that is based upon cash units where each is controlled by a private key.

## 2. Coin distribution.
I2Cash is given to Anoncoin and Bitcoin holders, 1:1000000 whatever, TBD. New cash units are created by verifying transactions. Issuance of new cash units will be gradually reduced until we have a total of X million cash units.

## 3. Distributed hash table (DHT).
Instead of a blockchain, I2Cash has a distributed hash table with a list of all cash units. This DHT is used to check if a cash unit is valid when people want to spend it. Once a cash unit changes ownership it will be updated in the DHT.

## 4. Verification nodes and Proof of Bandwidth.
The network is being kept secure by verification nodes. To become a verification node you have to initially route a certain amount of bandwidth as an I2P node. You have to keep routing traffic for the I2P network to stay a verification node. (Before PoB it is node age and reputation, maybe we keep this in as well? Can they stay a verification node for free? Seems risky.)

## 5. Distributed verification network.
These verification nodes form a distributed verification network following the Federated Bynzantine Agreement model. Quorum slices of nodes in this network collectively sign the cash units as valid or invalid. They use the the collective signing (CoSi) algorithm, an aggregate signature scheme based on Schnorr signatures and the EdDSA signing procedure.

## 6. Transactions.
If Alice wants to send money to Bob she signs the control of the cash units over to Bob. 
Etc...

## 7. Zero knowledge proofs.
Something about this? Where when why how? :)

