Proof Of Citation
===============

##Abstract

Acedimic paper sumbission

##Peer Review
In the current model the original author does not know whom reviews the paper, or what their intrests are.

##Revisions
Revisiosn are not made public, only the final edited work is published.

Solution
Using coloured / colored coins to submit document SHA256 hashes into the block chain via the OP_RETURN field.

##Normalised
The meta data side change should be normailised to keep chains small.  Also, subscribers of the chain may only wish to download information that is of relevance.  Data should be nomailsed into XML structures.

Why XML?

##Categories
Categories can be submitted by

```xml
<Category Lang="en-au">
    <Name></Name>
    <Parent>hashofprevious</Parent>
</Category>
```
Todo: XML schema

Authors
The author structure contains the authors bitcoin public key, and is signed with the private key for that address.

Create the structure
```xml
<author>
<name>Lucas Cullen</name>
<bio>https://www.bitcoinbrisbane.com.au</bio>
<contacts>
<contact type="email">lucascullen@hotmail.com.au</contact>
</contacts>
<publickey>04c5e26011bd1680eff56a6ec50301e2a06e87cff792c9058e8b692cb47488a18b1d9e509d31c5b98248d9aed24e70512ef3b054f2f02afc8f5b54db5b3516fa0a</publickey>
<address>16ZFPHneWK8umY2KbGSWm861uaL3q82dFw</address>
</author>
```
SHA-256
Create the hash of the document using SHA-256.  Add the value as an attribute on the author.
```xml
<author sha256="240934ec86f17126178e48c8c90d212bfca18148b30e2ff8ded1b51a662c80cf">
<name>Lucas Cullen</name>
<bio>https://www.bitcoinbrisbane.com.au</bio>
<contacts>
<contact type="email">lucascullen@hotmail.com.au</contact>
</contacts>
<publickey>04c5e26011bd1680eff56a6ec50301e2a06e87cff792c9058e8b692cb47488a18b1d9e509d31c5b98248d9aed24e70512ef3b054f2f02afc8f5b54db5b3516fa0a</publickey>
<address>16ZFPHneWK8umY2KbGSWm861uaL3q82dFw</address>
</author>
```

Sign the document and add attribute to the author element.

```xml
<author sha256="240934ec86f17126178e48c8c90d212bfca18148b30e2ff8ded1b51a662c80cf" version="Bitcoin-qt (1.0)" signature="G0xzGNeKfEwPz34Dr5lFwUhyCkj+KKSQGcaeQJ44cxzYPmVRJjw6kBgBBGwsnIWA0oqMrJAXJCNpbwW8anHaTjY=">
<name>Lucas Cullen</name>
<bio>https://www.bitcoinbrisbane.com.au</bio>
<contacts>
<contact type="email">lucascullen@hotmail.com.au</contact>
</contacts>
<publickey>04c5e26011bd1680eff56a6ec50301e2a06e87cff792c9058e8b692cb47488a18b1d9e509d31c5b98248d9aed24e70512ef3b054f2f02afc8f5b54db5b3516fa0a</publickey>
<address>16ZFPHneWK8umY2KbGSWm861uaL3q82dFw</address>
</author>
```
Other:
Tip for commit address
