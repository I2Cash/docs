# ANC -> Cash FAQ

**Last updated: 8/Feb 2018**

Note: The content of this document is subject to change. We will let you know through this document when it's final

## Questions

### What is I2Cash?

Quoted from the whitepaper's abstract:

Here we will introduce a digital analogue of cash concept, the next generation cryptocurrency. 
The key property of cash is anonymity: when you take money out of the bank, the bank gives you the cash without knowing what you buy, and when you spend money, the merchant has no idea who you are. By contrast, when you buy something with a credit card online, you have to tell the merchant who you are, and you have to tell the credit card company who you are making a purchase 
from. The same case exists in current blockchain based cryptocurrencies like Bitcoin. 
The potential for invasion of privacy is immense. Some of the existing cryptocurrencies like 
Monero, Zcash and more currencies try to anonymize their users with solving the traceability 
upon the blockchain which is based on an open ledger of transactions. In this paper, we introduce 
a new form of cryptocurrency without a blockchain or DAG, and is not built upon transactions but 
rather the cash units.

### What technologies from other cryptocurrencies do we use?

* Federated Byzantine agreements, is also found in Stellar.
* Schnorr signatures is connected to the segwit patch for Bitcoin.
* Elliptic Curves - found in all of them.
* GOST - found in GOSTcoin(?).
* (Non Interactive) Zero Knowledge Proofs - found in Zcash.

### What about people owning ANC at the moment? 

Cash will be credited to all ANC holders. We will take a snapshot of the blockchain at a certain height and credit Cash based on this. The exact blockchain height is yet to be decided.

### If I have 10 ANC, how much Cash will I get?

This decision on the ratio of ANC to Cash has not been made. We are listening to the voice of the community for this. You can [come to our Slack and join the discussion.](https://join.slack.com/t/anoncoin/shared_invite/enQtMjcxMzUxMjk5ODYwLTU0OTJhNmIxNzYyY2JiMzUxOGZhMjYzNmQ3YmViNWM1OWIxZGNlMGY0Zjg1NzdhMDAyZmRiYTFhNTM1OWZiYTU)

This document will be updated once we have decided this.

### Will holders of Bitcoin get Cash as well?

This has been discussed, but it has not been decided. We are listening to the voice of the community for this as well. If we decide to do this, we will take a snapshot of the blockchain at a certain height and credit Cash based on this.

### Is there a whitepaper out?

We're working on getting a draft ready for public view. We have some decisions to make before we release the paper. However, the core design of the system is done.

### Will there be transactions fees?

Initially there will probably not be any transaction fees. We have some ideas and draft on how this can be done.

### I can't sync my ANC wallet!

Don't panic - We know of this issue and will release a version fixing this before we take the snapshot for I2Cash.

### Is this actively developed?

Yes, we're implementing it as you write this. Code will be released when we are ready.

### What languages are used?

We'll use JS as our choice of Proof of Concept language. C/Rust will be used for production implementation.

### Is this secure?

As long as Elliptic Curves are considered safe yes. Note that breaking Elliptic Curves would invalidate all crypto currencies and not just this. This includes Bitcoin.

### Which curves are evaluated for this?

Nodes use ed25519 keys.

In other parts we use the famous secp256k1 which Bitcoin uses - we're also looking into a 
short Weierstrass version of curve25519.

### Where can I learn more about Elliptic Curves?

Math courses, the internet and in books.
A good place to start is [this article.](https://eng.paxos.com/blockchain-101-foundational-math)

You can also [check out our link section here.](https://github.com/I2Cash/project/blob/master/Links.md)


### Is there a forum to discuss this on?

Soon, will update this post with a link. Other than that, we use the ANC slack.
[Click here to join our Slack.](https://join.slack.com/t/anoncoin/shared_invite/enQtMjcxMzUxMjk5ODYwLTU0OTJhNmIxNzYyY2JiMzUxOGZhMjYzNmQ3YmViNWM1OWIxZGNlMGY0Zjg1NzdhMDAyZmRiYTFhNTM1OWZiYTU)

### What relation does this have with I2P?

Nothing besides that Meeh, is working on both systems. However, we will propose protocol change in I2P which will allow the mining process be proof of tunnel participation/bandwidth. In other words, mining is helping the I2P network 
with bandwidth and stable nodes.

### Wait what, Proof of Tunnel Participation?

Yes, read about the I2Path concept;

I2Path is a secure bandwidth measurement mechanism that utilizes decentralized groups of I2P "Cash server" routers extending I2P's existing "Floodfill routers", to assign each client an I2P tunnel that is publicly verifiable, but privately addressable. 
This mechanism allows I2Path to "sign" newly-minted Cash which can be checked 
towards the inflation reserve.

#### Will this come at the same time as I2Cash itself?

No, this will be added at a later stage if accepted by I2P. It would require minor 
modifications on the I2P routers.

#### Security Considerations

##### Anonymity

The I2Path protocol guarantees that no single router knows any client's entire tunnel. If malicious clients or routers collude, they may be able to shrink the anonymity set to the set of honest routers and clients in the consensus group. Groups can have varying sizes, however, allowing clients to 
choose the desired balance between anonymity threshold and tunnel assignment delay.

##### Group Formation

The I2Path protocol’s random tunnel selection mechanism prevents colluding I2P routers from
deterministically placing themselves in the same tunnel, provided not too many participants in each group collude. Even if half of the temporary keys in matrix M are held by colluding participants, 
for example, only 1/2 4 = 1/16 of the assigned tunnel will be compromised and able to mint (a limited number of) Cash without performing useful work. We could add further protection against "flash mobs" 
of colluding participants by randomizing group assignment across longer time periods, instead of using temporal locality as the only grouping criterion.

##### Tunnel Diversity

I2Cash's Neff shuffle could assign the same relay to one tunnel in multiple positions: e.g., choose the 
same physical "tunnel participant" router as both entry and middle "tunnel participant" router. With a 
reasonable number of participating "tunnel participant" routers, however, it should be extremely unlikely 
that one router gets assigned to all three positions on the same tunnel. In any case, the risk of accidental 
router duplication on one path should not be substantially greater than the risk I2P users already face of 
randomly placing multiple routers owned by the same operator on a tunnel. We anticipate that 
privacy-preserving independence testing techniques [16] could be adapted to detect and reject tunnels 
in which the same "tunnel participant" router (or operator) appears multiple times, but we leave this 
challenge to future work.

##### Persistent Guards

The assignment process above picks three routers afresh for each tunnel, contrary to I2P's practice of keeping 
entry routers persistent for longer periods. The tunnel assignment mechanism could be adapted for persistent 
entry routers by combining the first two columns of matrix M into one column representing each client together 
with its choice of entry router, at the cost of slightly increasing the chance of forming all-compromised tunnels.