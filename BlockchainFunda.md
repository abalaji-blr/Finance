#  Blockchain Fundamentals

[TOC]

---



## Resources

* [Block Chain Fundatmentals - Youtube Playlist](https://www.youtube.com/playlist?list=PLxVihxZC42nF_MCN9PTvZMIifRjx9cZ2J)
* [Free Coursera Course - Bitcoin and Cryptocurrency Techonologies By Arvind Narayanan](https://www.coursera.org/learn/cryptocurrency)
* [New Directions in Cryptography - Asymmetric Encryption - Public and Private keys](https://ee.stanford.edu/~hellman/publications/24.pdf)
* 



---

## Crypto in Cryptocurrency?

### What is "Double Spend" Problem?

This is specific to **digital currency**. The person can try to spend the same digital currency for multiple things. This multiple spend using the same currency can be detected at the later stages of the processing and that would be too late for any actions. So, there is a need to avoid this problem and it is done using cryptography. Thus it is called as crypto currency.

---

### How the Cryptocurrency solves the "double spend" problem?

**By verifying the transactions**. Checks to see whether the currency with ID is already spent or not. If not spend, it will be added to the transaction list. If not it will be rejected.

---

### What kind of encryption is used in cryptocurrency?

Cryptography uses asymmetric encryption - ie., generates the **public and private (secret) keys**. As indicates, the public key is **visible or known** to all, whereas the **private** is a **secret** key that needs to be kept secret. By mistake, if the secret key is revealed, anybody can steal the digital currenycy.

---

### What is Hashing?

Hashing is a process of converting the input into a value. The **output value** is called as **hash.** The function which converts the input value to output is called as **hash function**.

For a good hash function, it should be **one way transformation**. In other words, from the hash, one should not be able to generate the input.

Note that the different inputs can result in **same hash**, which is called as **collision**. There are many to resolve the collisions.

Some popular cryptographic hashes are:

* MD5 - Message Digest algorithm 5 - Generates hash of width 128 bits (16 bytes)
* SHA1 - Secure Hash Algorithm 1 - Generates 160 bits (20 bytes) of hash value
* SHA2 - Consists of six hash functions, which means can generate six hashes including SHA-256.

---

### What is a Hash Pointer?

Hash Pointer is a data structure which contains two components. One component is a **pointer** to the data and the second component is **hash value** of the data.

One application of the Hash Pointer in Block-chain is to **tamper proof**. If the adversary is trying to modify the content of the block, which will result in different hash value. If the adversary tries to update the hash value as well all the way up to **genesis** block but adversary can't update the pointer what the **genesis** block pointing to. Thus it is tamper proof.

For more info - [read this medium article](https://medium.com/@zhaohuabing/hash-pointers-and-data-structures-f85d5fe91659).

---

### What is Merkel Tree?

Merkel tree is a binary with **hash pointers**. The leaf nodes holds the **data** blocks. The other nodes are **hashes** of their respective children.

We can make the Merkel tree sorted, which can help in finding whether the data block is present or not in the given tree in efficient way. For identifying the membership, it takes $O(log\ n)$ time when compared with $O(n)$ in the case of linked list implementation.

For more info - [read this medium article](https://medium.com/@zhaohuabing/hash-pointers-and-data-structures-f85d5fe91659).

---

### What is Digital Signature?

Digital Signature is another primitive in block chains. It's a mathematical technique to validate the authenticity and integrity of the message or digital document.

A digital signature scheme consists of following three algorithms:

* **(sk, pk) = generateKeys(keySize)**
  * The input keySize is to specify the size of the keys which is to be generated.
  * The output **sk** is a **secret key**, which needs to be kept **privately** and used to sign messages.
  * The output **pk** is a **public key**. 
* **sig = sign(sk, message)**
  * **sign()** method takes secret key and message  as input.
  * Outputs a **sig** - signature for the message undersecret key. The length of the **sig** is similar to length of **secret key**.
* **isValid = verify(pk, message, sig)**
  * **verify()** method takes public key, message and signature.
  * Outputs the boolean value, **isValid**, that will be **tue** if sig is a valid signature for the message under public key pk, and **false** otherwise.

---

### What is the Digital Signature used in Bitcoin?

Bitcoin uses a particular digital signature scheme known as **Elliptic Curve Digital Signature Algorithm** ( **ECDSA**). 

For more info, [check Wikipedia](https://en.wikipedia.org/wiki/Elliptic_Curve_Digital_Signature_Algorithm)

---



## Distributed Consensus

### What are the factors which make the distributed consensus hard?

* Nodes may crash
* Nodes may be taken over by malware
* Latency on the network

### How Bitcoin is able to reach distributed consensus?

* Providing financial incentives which make the participants work together.
* Arrive consensus over a large time scale.

---

### What are the incentives for the block creators in Bitcoin?

Two separate incentive mechanisms are used in Bitcoin.

1) **Block Reward:**

   The node which creates a block gets to include a special transaction called **coin-creation** transaction in that block. **Every 210,000 blocks, the block creation reward is halved** (approx. every 4 years). It started with 50BTC during its inception in 2009. As of 2021, the block creation reward is halved for the third time at 6.25BTC.

   Aprox. year: 2000 ->  2013 -> 2017 -> 2020 ...

   Block creation Reward: 50BTC -> 25 BTC -> 12.5BTC -> 6.25 BTC ...

2) **Transaction Fee: ** 

   Once, the block reward runs out, a **transaction fee** (optional akin to tips) will be collected by the **block creators** aka **miners**.

---

### What is Proof of Work in Bitcoin?

As the block creation results in a reward and to avoid the nodes from gaming (manipulating) the system, the block creator node has to solve **hash puzzles**. The node has to find a **nonce (a small number, a number used only once)**, which needs to be concatenated with the previous hash value and all transactions and their hash value should be in the target space.

$H(nounce || previous\_hash || tx1 || tx2 || ... || tx) < target$

---

### What is Bitcoin mining?

The process of repeatedly trying and solving the **hash puzzles** is known as **Bitcoin mining**. It takes a lot of computing power (many trials) to find the **nonce** which can fall in the target space, which is outside the realm of possibility for a laptop. Hence, the nodes will deploy more powerful compute machines for mining. These nodes are called miners**. 

The mining process is expensive and that is one reason not all participate in mining. Due to the high cost of mining the power has been concentrated in the mining ecosystem.

---

## Mechanics of Bitcoin

### How Bitcoin blocks are represented?

Bitcoin block has a block header and **transactions**. 

The block header has the following: Hash from the prev block, metadata, nonce, and Merkel root.

The **Merkel root** holds all the transactions.

 [Check this blog for further details](https://marcsteiner.tech/blog/description-of-bitcoin-blocks-and-transactions)

![See this picture for visualization](https://upload.wikimedia.org/wikipedia/commons/7/7a/Bitcoin_Block_Data.png)



---



 





