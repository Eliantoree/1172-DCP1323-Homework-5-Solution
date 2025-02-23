# 1172-DCP1323-Homework-5-Solution
1172/DCP1323 Homework 5 Solution

**Download Link:https://programming.engineering/product/1172-dcp1323-homework-5-solution/**

Description
5/5 – (2 votes)
Part 1: Written Problems

Solve the following problems

Consider the Davies and Price hash code scheme described in Section 11.4 and assume that DES is used as the encryption algorithm:

= −1⨁ ( , −1)

Recall the complementarity property of DES (Problem 3.14): If Y = E(K, X), then Y′ = E(K ′,X′). Use this property to show how a message consisting of blocks 1, 2, … , can be altered without altering its hash code.

Show that a similar attack will succeed against the scheme proposed in [MEYE88]:

= ⨁ ( −1, )

Now consider the opposite problem: using an encryption algorithm to construct a one-way hash function. Consider using RSA with a known key. Then process a message consisting of a sequence of blocks as follows: Encrypt the first block, XOR the result with the second block and encrypt again, etc. Show that this scheme is not secure by solving the following problem. Given a two-block message B1, B2, and its hash

RSAH(B1, B2) = RSA(RSA(B1) ⊕ B2)

Given an arbitrary block C1, choose C2 so that RSAH(C1,C2) = RSAH(B1,B2).

Thus, the hash function does not satisfy weak collision resistance.

DSA specifies that if the signature generation process results in a value of s = 0, a new value of k should be generated and the signature should be recalculated. Why?

It is tempting to try to develop a variation on Diffie–Hellman that could be used as a digital signature. Here is one that is simpler than DSA and that does not require a secret random number in addition to the private key.

Public elements:

q

prime number

α

α < q and α is primitive root of q

Private key:

X

X < q

Public key:

Y = mod q mod q

To sign a message M, compute h = H(M), which is the hash code of the message. We require that gcd(h,q − 1) = 1. If not, append the hash to the message and calculate a new hash. Continue this process until a hash code is produced that is relatively prime to (q − 1). Then calculate Z to satisfy Z ≡ X × h(mod q − 1). The signature of the message is σ = . To verify the signature, a user compute t such that t × h = 1 mod (q − 1) and verifies Y = σ t mod q. Show that the scheme is unacceptable by describing a simple technique for forging a user’s signature on an arbitrary message.

1

Assume a technique for a digital signature scheme using a cryptographic one-way hash function

(H) as follows. To sign an n-bit message, the sender randomly generates in advance 2n 64-bit cryptographic keys: 1, 2, … , , 1′, 2′, … , ′ , which are kept private. The sender generates the following two sets of validation parameters which are made public.

, ,…,

′

, ′

,…, ′

1 2

1

2

where

= H(

||0),

′

= H( ′||1)

The user sends the appropriate

or ′

according to whetheris 0 or 1 respectively.

For example, if the first 3-bits of the message are 011, then the first three keys of the signature are 1, 2′, 3′

How does the receiver validate the message?

Is the technique secure?

How many times can the same set of secret keys be safely used for different messages?

What, if any, practical problems does this scheme present?

Part 2: Programming Problem

This programming problem is to simulate the bitcoin mining. Note that this is not the real bitcoin mining. It only verifies the difficulty of finding hash values with many leading zeros. You can use either OpenSSL or Crypto++. Nevertheless, using Crypto++ in Visual Studio is preferred. Please find the related library information and examples on the Internet.

Do sha2-256 (that is, sha256) on the following text, where the first row is the test sample:

Message (in ASCII)

Message digest (in Hex)

“Hello!”

334d016f755cd6dc58c53a86e183882f

8ec14f52fb05345887c8a5edd42c87b7

“Bitcoin is a cryptocurrency,

?

form of electronic cash.” II. Mine cryptocurrency:

Build the blockchain in the following table until the requirement of leading zeros cannot be met. We start with the hash value Sha256(“Bitcoin”) =

B4056DF6691F8DC72E56302DDAD345D65FEAD3EAD9299609A826E2344EB63AA4

# of leading

Preimage = Previous hash (in Hex)+

Hash value (in Hex), with the specified

zeros

Nonce (32 bits, in Hex)

leading zeros

0

B4056DF6691F8DC72E56302DDAD345D6

2767667C2AF3BE01EFAC4FB387EC27C1

5FEAD3EAD9299609A826E2344EB63AA4

0B9D3BEE9C5D48CFF4CFB9F523560B24

00000000

1

2767667C2AF3BE01EFAC4FB387EC27C1

0DE32E85C2AC9D96659D42C8A3EA3D2C

0B9D3BEE9C5D48CFF4CFB9F523560B24

05FDE384B468E6EFE062B6E21288CBCA

0000000A

2

?

?

3

?

?

…

?

?

2


Submission: you need to upload two files: hashchain.cpp and out.txt, where out.txt contains the chain in the form (the number of leading zeros, previous hash, nonce, current hash, …):

0

B4056DF6691F8DC72E56302DDAD345D65FEAD3EAD9299609A826E2344EB63AA4

00000000

2767667C2AF3BE01EFAC4FB387EC27C10B9D3BEE9C5D48CFF4CFB9F523560B24

1

2767667C2AF3BE01EFAC4FB387EC27C10B9D3BEE9C5D48CFF4CFB9F523560B24

0000000A

0DE32E85C2AC9D96659D42C8A3EA3D2C05FDE384B468E6EFE062B6E21288CBCA

…

Grading: the more leading zeros your hash values have, the higher your grade is.

On-site test: Will announce the venue and schedule later. You need to pass the onsite test to get the credits of this programming problem.

.

