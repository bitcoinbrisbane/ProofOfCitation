Proof Of Citation
===============

##Abstract

Acedimic paper sumbission... incentivise authors to submit quailty papers and reward them for this effort.
By creating a protocol for submitting papers will allow developers to create solutions...

##Peer Review
In the current model the original author does not know whom reviews the paper, or what their intrests are.

##Revisions
Revisiosn are not made public, only the final edited work is published.

##Solution
Using coloured / colored coins to submit document SHA256 hashes into the block chain via the OP_RETURN field.  XML documents, papers and images to be distributed using Storj https://github.com/Storj/

##Normalised
The meta data side change should be normailised to keep chains small.  Also, subscribers of the chain may only wish to download information that is of relevance.  Data should be nomailsed into XML structures.

Why XML?

##Categories
Categories can be submitted by

```xml
<Category Lang="en-au">
    <Name>Mathematics</Name>
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

Sign the document and add attribute to the author element.  *Note, this will create a different hash to what is stored in storj

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

The hash of the document is the generated using SHA256.  Eg 65cc3475c0119d907ef1a8c45c0488f4d82b1ca65a9443023e82119a1cadde28

This is the value that is entered to the OP_RETURN and used with storj.

###Paper structure
The xml document is a wrapper for the paper.  It provides indexable data and citations.

Authors
```xml
<authors>
<author sha256="240934ec86f17126178e48c8c90d212bfca18148b30e2ff8ded1b51a662c80cf"/>
</authors>
```

Paper structure

Citations
Papers are cited by sending a small (or large) bitcoin transaction from the papers public key to the address of the paper being cited.  This will "tip" the author for their paper.

```xml
<citations>
<citation id="1">693bf1445c13c9c75eb292b3dd7256cbbfa89f4efa805fd8571064de938ae146</citation>
</citations>
```

```xml
<paper address="3KLQEuNXM3ZLSHrDoi6qA9HAwGSzsjVAVc" title="First paper">
<citations>
...
</citations>
<authors>
...
</authors>
</paper>
```

Signing the paper
Each author then signs the paper, and adds their signature in the signature attribute of the author element.

Submit the paper


###Other:
Tip for commit address
