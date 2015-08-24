Bitcoin FS (Financial Services)
==========

Bitcoin FS is a patch set on top of Bitcoin XT fork of the Bitcoin Core, with a focus on upgrades to the peer to peer protocol. By running it you can opt in to providing the Bitcoin network with additional services beyond what Bitcoin Core provides that enable quicker adoption by Financial Services firms.

Currently plans for following additional changes:

1. *Support for larger blocks.* XT has support for BIP 101 by Gavin Andresen, which schedules an increase from the
   one megabyte limit Bitcoin is now hitting.  This distribution will increase the block size to 100mb.
2. Relaying of double spends. Bitcoin Core will simply drop unconfirmed transactions that double spend other unconfirmed transactions, forcing merchants who want to know about them to connect to thousands of nodes in the hope of spotting them. This is unreliable, wastes resources and isn't feasible on mobile devices. Bitcoin XT incorporates work by Tom Harding and Gavin Andresen that relays the first observed double spend of a transaction. Additionally, it will highlight it in red in the user interface. Other wallets also have the opportunity to use the new information to alert the user that there is a fraud attempt against them.
3. Support for querying the UTXO set given an outpoint. This is useful for apps that use partial transactions, such as
   the [Lighthouse](https://github.com/vinumeris/lighthouse) crowdfunding app. The feature allows a client to check that a partial SIGHASH_ANYONECANPAY transaction is correctly signed and by querying multiple nodes, build up some
   confidence that the output is not already spent.
4. DNS seed changes: bitseed.xf2.org is removed as it no longer works, and seeds from Addy Yeow and Mike Hearn are
   (re)added to increase seed diversity and redundancy.  FS uses the same data directories as Core so you can easily switch back and forth. You do *not* need to redownload the block chain.
5. Inclusion of AML/KYC features that can be decrypted by the intended financial services recipient
6. Blacklisted Bitcoin Addresses
7. SWIFT integration 
8. FIX/ Fast Protocol integration
9. Sola Access Information Language (SAIL) protocol integration 
10. High Speed Vendor Feed (HSVF) integration
11. MIT203 - Native Trading Gateway Interfacing options : http://www.londonstockexchange.com/products-and-services/millennium-exchange/millennium-exchange-migration/mit203issuev11-1.pdf
12. NYSE UTPDirect Protocol : https://www.nyse.com/publicdocs/nyse/markets/nyse/NYSEUTPDirect_Specification.pdf
13. SIEM Endpoints 
14. Regulatory Compliance Option for Financial Services Firms ensuring any FS companies buying, selling or trading bitcoin via Bitcoin FS client do so in compliance with their companies regulatory commitments.  This is a client side feature that will not affect the blockchain or existing bitcoin users.
15. Digital Forensics enhancing capabilities for Bitcoin FS clients
16. Biometric authentication

The FS Manifesto
================

Bitcoin FS incorporates changes that didn't make it into Core, or are very unlikely to, due to differing philosophies.

The principles FT uses to guide decisions on patches are as follows:

* We try to follow the founding vision of the Bitcoin project, as defined by Satoshi's writings. That means:
  * We support a Bitcoin network in which ordinary people settle with each directly on the block chain.
  * We aim for mainstream Financial Services adoption, by making it easy for the public to transact with Financial Services firms.
  * We focus on the user experience, as ultimately, how users experience Bitcoin is fundamental to the project's success.
* There is a clear decision making process, and product decisions are made in a timely manner.
* We maintain a professional working environment at all times. The developer discussion forum is moderated and
  troublemaking, nastyness, Machiavellianism etc will result in bans.
* We aim to provide features that enable easier and quicker adoption by companies constrained by AML/KYC regulation.

Development process
===================

To propose a patch for inclusion or to discuss Bitcoin development in general, (https://groups.google.com/forum/#!forum/bitcoin-fs-financial-services).

The repository has a similar structure to upstream, however, because patches are constantly rebased every release
has a branch including the minor ones. FS releases use the upstream version with a letter after them. If two releases
are done based on the same upstream release, the letter is incremented (0.11.0A, 0.11.0B etc).

Possible future features
========================

Ideas for useful protocol upgrades are tracked in the issue tracker.

Bitcoin FS is intended to be compatible with crowd funded and financial services development. If you would like to experiment with a (non consensus changing) protocol upgrade, please discuss it on the mailing list first. You should be able to get a clear decision on the concept and design before starting on the implementation.
