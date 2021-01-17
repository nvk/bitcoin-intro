---
title: Bitcoin Backups
filename: backup.md
--- 


# Bitcoin Backups

You (and only you) are responsible for making bitcoin wallet backups - this document will guide you through this process.
- Backup Overview
- Backup Methods
- Encrypted Backups
- Backup Checking
- Backup Recovery
- Common Questions

# Backup Overview

A bitcoin wallet backup is a complete set of information from which your bitcoin can be recovered. 

For a typical single signature wallet this information is the `ordered seed words`, the `derivation path(s)` and possibly a `passphrase`. 

```
SINGLE SIG WALLET BACKUP    =   ORDERED SEED WORDS
                                DERIVATION PATH(S)
                                PASSPHRASE
```

## 1. Ordered Seed Words

12 or 24 words shown to you at the point of creating your bitcoin wallet and often visible in your bitcoin wallet under the name seed / backup.

These words are often called `seed words` because they encode your bitcoin seed.

**The order of the seed words is critical** - make sure to number the words as you write them down and check that the order matches that shown in the wallet.


```
 RECORD THE ORDER OF SEED WORDS

----- DO -----		-- DON'T --
1. Seed Word 1		Seed word 3
2. Seed Word 2		Seed word 1
3. Seed Word 3		Seed Word 2
```

## 2. Derivation Path

The seed words alone are often insufficient to recover your bitcoin using different bitcoin wallet software. 
This is because there are many different valid derivation paths and the seed words don't specify which derivation path was used by your wallet. 

For this reason it is best practice to **record the derivation path** in addition to the seed words when making a backup.
To find the derivation path used by your wallet look for your wallet on [walletsrecovery.org](https://walletsrecovery.org/) or look for this information within your wallet / the documentation which is typically found on the wallet website or GitHub page.

If you have a seed but no record of the derivation path you can either look-up the derivation paths used by your wallet (if you remember which one you used), or use a wallet that scans many different derivation paths until it finds bitcoin (e.g. Electrum).

## 3. Passphrase

Some wallets (e.g Samourai Wallet & ColdCard) allow the user to set a custom `passphrase`.

A backup for this type of wallet must contain the `ordered seed words`, the `derivation path` and the `passphrase`.

The main benefit of a passphrase is that you can have multiple wallets which are completely separate but which share a common `seed phrase`. 

```
ORDERED SEED WORDS  +  PASSPHRASE 1 = WALLLET 1
                    +  PASSPHRASE 2 = WALLLET 2
                    +  PASSPHRASE 3 = WALLLET 3

            (AT A SPECIFIC DERIVATION PATH)
```

This is convenient - A backed up seed phrase (on metal and on paper in multiple locations) can be re-used for many wallets.

If you used a strong passphrase is not possible to recover your bitcoin if you lose it. 
If you use a weak passphrase it may be able to guess it (through trial end error), although this should not be relied upon.

# Backup Methods

We strongly recommend that you avoid the following backup methods:
- Memorisation
- Screenshots
- Loose scrap of paper
- Single copy backups
- Only digital backups

## Minimum Viable Backup

We recommend **as a minimum** that you make at least two paper backups stored in separate envelopes addressed to yourself. 
These should contain your seed words, the derivation path(s) and your passphrase(s) if used.

This will protect you against the most common way of losing bitcoin which is losing your backup, but will not protect you against theft.
If you can't reasonably expect that a location is secure, we recommend that you use a multi-location backup.

## Suggested Backup

To protect your bitcoin against trivial theft you must avoid single location backups in locations which you can't reasonably expect to be secure.

In our experience bitcoin is most frequently lost, rather than stolen, so avoid complicated backup methods which require significant time, complexity or specialist equipment.

We recommend splitting the backup into two parts, A & B.
Each part should be stored on paper in an envelope addressed to yourself or stamped on metal.

| Part | Passphrase Approach |
| ---  | --- |
| A | The seed words and the derivation path  |
| B | The passphrase |

We recommend that you store at least two copies of A (in different locations) and at least two copies of B (in different locations). 

Ideally these would be 4 unique, secure geographic locations which you can reasonably expect to be able to access indefinitely.
In practice, they might be in 4 unique locations within one geographic area, but with each item well hidden.

A wallet backup can be reliably stored unencrypted by being written on paper or stamped into metal.

## Paper Backups

When making a paper backup:
- Avoid pencil
- Write seed words in both lower case and uppercase
- Number each seed word
- Increase the durability of the backup by laminating it
- Use waterproof ink & paper
- Put it in a sealed envelope addressed to yourself - It is unlikely that you, or anyone else, will dispose of an unopened addressed envelope.

## Metal Backups

There are many types of metal backup - [this DIY solution](https://twitter.com/econoalchemist/status/1329271917539254272) is simple, low cost and effective. You will need; 
- A metal stamp set of numbers and letters
- Stainless steel washers
- A nut and bolt
- A hammer and hard surface

When making a metal backup this way:
- Use stainless steel to avoid corrosion over time
- Use a tool / jig to position the letters 
- Use hard impacts with the hammer to indent deeply
- Minimise the number of impacts to improce legibility

Alternately you can buy one of [the many products](https://jlopp.github.io/metal-bitcoin-storage-reviews/). 
If you do this do not get it shipped to your real address, use a temporary email address if required and pay in a way that keeps you private.
Due to these nuances we recommend using the DIY approach.

# Encrypted Backups

A wallet backup can be encrypted using digital or physical encryption tools.

## Digital Encryption

Digital encryption allows you to encrypt your data using software on a computer. Examples include [ColdCard's MicroSD card backups](https://coldcardwallet.com/docs/backups) & more generic encryption tools such as [VeraCrypt](https://www.veracrypt.fr/en/Home.html).

Typically the data will be encrypted with a password, although some tools allow you to any digital file (such as an image) as the encryption key.

The computer on which the data is encrypted / decrypted must be secure, otherwise the backup could be copied by malware.

The easiest way to do this is to use a dedicated device (such as a ColdCard) or use temporary OS like [tails](https://tails.boum.org) on an computer which is not connected to the internet.

## Physical Encryption

Physical encryption allows you to encrypt your data using a physical mechanism or device. Examples include the [Enigma machine](https://en.wikipedia.org/wiki/Enigma_machine) famously used in WW2 and the [revealer](https://revealer.cc/) optical encryption device.

Ensure that any physical encryption tool is commonly available so that you can decode when required - don't use an Enigma Machine!

## Manual Encryption

Data can be manually encrypted using a scheme such as a [One Time Pad](https://en.wikipedia.org/wiki/One-time_pad)). 
Although this provides perfect encryption but is time consuming to encode / decode a wallet backup this way.

 ColdCard user example
- A ColdCard wallet with a passphrase
- Seed on a metal backup in location A
- Derivation path & passphrase on a metal backup in location B
- Encrypted Micro SD card backup in both locations
- Decryption key in location C

## Implementing an Encrypted Backup

We only recommend the encrypted backup approach for ColdCard users, technical experts or users of wallets which create encrypted backups automatically. 

Due to the added complexity of making, storing and recovering an encrypted backup we recommend that you **also keep an unencrypted backup** as described above. 

| Part | Encryption Approach |
| ---  | --- |
| A | Encrypted File | 
| B | Decryption Key |

We recommend that you store **at least** two copies of A (in different locations) and at least two copies of B (in different locations). 

Ideally these would be 4 unique, secure geographic locations which you can reasonably expect to be able to access indefinitely.
In practice, they might be in 4 unique locations within one geographic area, but with each item well hidden.

# Backup Checking

Always check your backup when making a new wallet. 
Failure to do so could lead to you losing your bitcoin. 

## How to check a backup

Software Wallet:

0. Download a bitcoin wallet and select create new wallet
1. Write down your seed words (in order), the derivation path and the passphrase used (if you set one)
2. Go to the receive section of your wallet and write down the first 15 characters of the address
3. Delete the wallet
4. Re-install the wallet and select recover existing wallet
5. Enter seed words, derivation path and passphrase where applicable 
6. Repeat step 2 and check that the address generated is the same

Hardware Wallet:

If using a coldcard you can verify that the file was not truncated or damaged in transit ([source](https://coldcardwallet.com/docs/backups)) but to fully check you should recover on a second device and check the address at a specific depth matches, or record the address at a specific depth then wipe the device and recover. 

# Backup Recovery

You should consider how much risk you can tolerate when recovering a wallet. 

As a general rule you should not recover your backup on a potentially insecure computer (your normal computer / your normal phone) unless you know the risks.
If the computer has malware or you downloaded a fake wallet then your bitcoin will be stolen.

If you know that the backup contains a small amount of bitcoin you may be comfortable recovering your backup using a reputable bitcoin wallet on your phone / desktop.

The most secure way for non-technical people to recover their backup is to buy a 'Hardware Wallet' such as a ColdCard and enter the seed into the device.

Another option is to recover on a temporary OS like [tails](https://tails.boum.org) on an computer which is not connected to the internet.

## Checking Frequency

You should always check your backup at the point of making it.

If you are using the wallet regularly, you do not need to verify that the backups are valid, just that they are still where you left them. 

Check that the backups are in location at irregular intervals, especially if using a backup split over multiple locations.
Don't regularly check backups (e.g. the 1st Jan each year) as this could be obvious and lead to people discovering your backup.

More reading on this subject: [SmartCustodyWhitePapers](https://github.com/BlockchainCommons/SmartCustodyWhitePapers/blob/master/%23SmartCustody-_Simple_Self-Custody_Cold_Storage_Scenario.md)

# Common Questions

## I only have a small amount of bitcoin, should still make a backup?
The value of bitcoin could increase substantially. 
For this reason we recommend that you always record your seed words and passphrase (if used). 
We recommend that you also record the derivation path, providing a full backup.

## Can I recover my bitcoin without the seed words?
If you have an encrypted backup that you can decrypt then you can recover your bitcoin.

If you don't then it is not possible to recover your bitcoin without the seed words.

## Can I recover my bitcoin without the passphrase?
Possibly.

If you used a weak passphrase it may be possible to brute force your passphrase using a script. 

We will link to one here when we find one we can recommend.

If you have forgotten the passphrase used for a wallet which you can still access (e.g. You know the pin for your wallet, and can therefore spend from it, but you do not know the passphrase) we recommend that you immediately send your bitcoin to a new wallet which you have fully backed up. 

If your wallet has coin control we recommend that you send each utxo to a new address generated by your new (backed up) wallet - this is better for privacy than sending all at once.

## Can I recover my bitcoin without the derivation path?
Likely, with some effort.

If you know which wallet you used you can look up the derivation paths on walletsrecovery.org.

If you used a common derivation path it may be possible to brute force your derivation path using a wallet with this functionality (for example, electrum). 

## What is a duress wallet?
You could store some of your bitcoin using a null passphrase and most of your bitcoin in a wallet which uses a passphrase. 
A thief / attacker who obtains your seed words will take your bitcoin and be unaware that you have access to additional funds using your passphrase.

Alternately, can make a wallet using a passphrase which you intend to give out to attackers in the case of duress (i.e. kidnapping).
You should pre-fund this with some bitcoin to make it believable.

## Should I split my seed words between locations? 

If you split 24 seed words into 3 partial lists, you can recover the full list of ordered seed words with only 2 of the 3 partial lists, giving some redundancy.


| Seed Words    | List A    | List B    | List C    | 
| ---           | ---       | ---       | ---       |
| 1 - 8         | X         |           |  X        |
| 9 - 16        | X         | X         |           |
| 17 - 24       |           | X         |  X        |

This method is simple and can be done manually (unlike Shamir's Secret Sharing which requires code) but unlike SSS a partial list may be vulnerable to brute force attacks.

The relationship between number of revealed seed words and security against brute force attack is not linear, and it is possible to brute force 4 / 12 words (whereas it we do not believe that it is likely that someone will brute force 8 / 24 seed words).  

For this reason we only recommend doing this with a 24 word seed. 
Ensure you number each seed word to make recovering the list easier

## What is a HD Wallet?

Almost all modern bitcoin wallets are 'HD' (Hierarchical Deterministic) wallets which means that you only need to record the `seed words`, `derivation path` and `optional passphrase` to recover your bitcoin. A single bitcoin private key is used to generate as many key pairs as are required. This makes it easy for the user to use a new address each time they receive bitcoin, which is how bitcoin is designed to be used.

Originally bitcoin wallets generated private keys at random, which meant that you had to make a copy of your wallet file regularly to make a full backup.

With a HD wallet the bitcoin private key (which is derived from the seed) is combined with a 'chain code' to generate what is referred  to as a 'master extended key'. For more details see [BIP32](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki).

Typically when backing up a wallet you are presented with the mnemonic seed - a series of either 12 or 24 words from [this list](https://github.com/bitcoin/bips/blob/master/bip-0039/english.txt) - it is an encoded version of your seed made to be easy to read and transcribe. The encoding method is detailed in [BIP39](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki#), but effectively each word on the wordlist corresponds with a number, and thus your 12 or 24 word mnemonic seed is simply an easy to write representation of a large number (your seed).

Many wallets label the mnemonic seed as just the 'seed' - take care, the mnemonic seed can be extended with an additional word or sentence (a passphrase), without which you cannot decode the actual seed (a 256 bit number) and thus, you cannot recover your bitcoin.