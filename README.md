Proof Of Citation
===============

##Abstract

Acedimic paper sumbission... incentivise authors to submit quailty papers and reward them for this effort.
By creating a protocol for submitting papers will allow developers to create solutions such as online paper viewers and browers, managed wallets, desktop and mobile apps.

##Peer Review
In the current model the original author does not know whom reviews the paper, or what their intrests are.

##Revisions
Revisions are not made public, only the final edited work is published.

##Solution
Using coloured / colored coins to submit document SHA256 hashes into the block chain via the OP_RETURN field.  XML documents, papers and images to be distributed using a provider such as Storj https://github.com/Storj/

##Normalised
The meta data side change should be normailised to keep chains small.  Also, subscribers of the chain may only wish to download information that is of relevance.  Data should be nomailsed into XML structures.

Why XML?

##Coloured Coins / Colored Coins
Different coloured coins https://github.com/OpenAssets/open-assets-protocol/blob/master/specification.mediawiki for document types;

1. Categories
2. Authors
3. Papers

##Taxonomy of a submission
The following a valid Submission types
1. Categories
2. Author
3. Paper

###Categories
Categories can be submitted by...  Note, sub coloured coins could be used for "high level" categories to make parseing more efficient.  A user online intrested in mathematical science may not wish to download other sceintific papers.

```xml
<Category Langauge="en-au">
    <Name>Mathematics</Name>
    <Parent>hashofprevious</Parent>
</Category>
```
Todo: XML schema

###Author
The author structure contains the authors bitcoin public key, and is signed with the private key for that address.

Create the structure
```xml
<Author>
<Name>Lucas Cullen</Name>
<Bio>https://www.bitcoinbrisbane.com.au</Bio>
<Contacts>
<Contact type="email">lucascullen@hotmail.com.au</Contact>
</Contacts>
<Publickey>04c5e26011bd1680eff56a6ec50301e2a06e87cff792c9058e8b692cb47488a18b1d9e509d31c5b98248d9aed24e70512ef3b054f2f02afc8f5b54db5b3516fa0a</Publickey>
<Address>16ZFPHneWK8umY2KbGSWm861uaL3q82dFw</Address>
</Author>
```
SHA-256
Create the hash of the document using SHA-256, and wrap the Author document in Submission tags.
```xml
<Submission type="Author" sha256="240934ec86f17126178e48c8c90d212bfca18148b30e2ff8ded1b51a662c80cf">
<Author>
<Name>Lucas Cullen</Name>
<Bio>https://www.bitcoinbrisbane.com.au</Bio>
<Contacts>
<Contact type="email">lucascullen@hotmail.com.au</Contact>
</Contacts>
<Publickey>04c5e26011bd1680eff56a6ec50301e2a06e87cff792c9058e8b692cb47488a18b1d9e509d31c5b98248d9aed24e70512ef3b054f2f02afc8f5b54db5b3516fa0a</Publickey>
<Address>16ZFPHneWK8umY2KbGSWm861uaL3q82dFw</Address>
</Author>
</Submission>
```

Sign the document and add the signature attribute to the Submission element.  *Note, this will create a different hash to what is stored in storj

```xml
<Submission type="Author" sha256="240934ec86f17126178e48c8c90d212bfca18148b30e2ff8ded1b51a662c80cf" version="Bitcoin-qt (1.0)" signature="G0xzGNeKfEwPz34Dr5lFwUhyCkj+KKSQGcaeQJ44cxzYPmVRJjw6kBgBBGwsnIWA0oqMrJAXJCNpbwW8anHaTjY=">
<Author>
<Name>Lucas Cullen</Name>
<Bio>https://www.bitcoinbrisbane.com.au</Bio>
<Contacts>
<Contact type="email">lucascullen@hotmail.com.au</Contact>
</Contacts>
<Publickey>04c5e26011bd1680eff56a6ec50301e2a06e87cff792c9058e8b692cb47488a18b1d9e509d31c5b98248d9aed24e70512ef3b054f2f02afc8f5b54db5b3516fa0a</Publickey>
<Address>16ZFPHneWK8umY2KbGSWm861uaL3q82dFw</Address>
</Author>
</Submission>
```

The hash of the document is the generated using SHA256.  Eg 65cc3475c0119d907ef1a8c45c0488f4d82b1ca65a9443023e82119a1cadde28

This is the value that is entered to the OP_RETURN and used with storj.

###Paper structure
The xml document is a wrapper for the paper.  It provides indexable data and citations.

Authors
```xml
<Authors>
<Author sha256="240934ec86f17126178e48c8c90d212bfca18148b30e2ff8ded1b51a662c80cf"/>
</Authors>
```

Citations
Papers are cited by sending a small (or large) bitcoin transaction from the papers public key to the address of the paper being cited.  This will "tip" the author for their paper.

```xml
<Citations>
<Citation id="1">693bf1445c13c9c75eb292b3dd7256cbbfa89f4efa805fd8571064de938ae146</citation>
</Citations>
```

```xml
<Paper address="3KLQEuNXM3ZLSHrDoi6qA9HAwGSzsjVAVc" title="First paper">
<Authors>
...
</Authors>
<Documents>
<Document provider="storj">75c766e2e2530d5f255954f3de784ef5997643200ac2b19c0b465cfd08247aa3</document>
<Documents>
<Citations>
...
</Citations>
</Paper>
```

Signing the paper
Each Author then signs the paper, and adds their signature in the signature attribute of the author element.

Submit the paper to provider

##Peer review
A review of a paper, is to simple cite and modify.

##Role of the software
1. Parse the bitcoin block chain looking for values in the OP_RETURN field.
2. Download the meta data from the storage provider, such as storj and persist in local database if required.
3. To provide users with an indexable and searchable interface.
4. Show repuation.  A commonly cited paper should be of high value, such as Satoshis White Paper.
5. Cointain coloured coins and provider tokens to enable users to submit work.

##Author reputation
Todo:

##Risks
Gaming the system...

##Discussion
Latex format for paper is to be considered.

###Other:
Tip for commit address
