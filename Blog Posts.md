POST 1

What is blockchain?
Blockchain is essentially a datastore, it is a very safe datastore.Its public, its just like a database
There are only 2 things you can do with it
You can either write to it and read from it
How to write to it?
You come up with a transaction of something that has to be written to a blockchain,and you are going to send it to the distributed system or the blockchain. It goes over there and all of the info is collected together and put together in whats called a “block” , inside a block they are put in smaller “package”. And this package is sent to what is called a “verifier”.so these verifiers look at the content of the transactions in this one block, all the them. And they are going to ensure that they satisfy the rules defined by the blockchain. For instance if we are talking about currency we confirm that the sender has the amount he is sending to confirm the transaction, rules like that, verifiers verify everything. After verification verifiers send this “signed or confirmed” info back to the blockchain or the “greater network”. So that is essentially blockchain.so just like that there will be some other blocks and they will be connected to each other through  a chain and so on and so forth. they will be linked together throught a series of operations. So in essence this is what a blockchain is. You keep on adding to the blockchain and this keeps on growing and is available publicly to everyone. So that is what a public blockchain. At each given instance we need to confirm that transactions are actually being made and all the rules are being followed. That is job  of all the different verifiers that keep the blockchain running. That is basically how a blockchain works.
Obviously there is alot more to it.

Wallet:
Think of the wallet as your “identifier” it has two parts 
A public key 
A private key 
A public key: is what you share with everyone hence the name “public” and everyone can identify you via that. Whenever you say that forexample  a wallet “9890809” is completing a transaction  we actually mean that a person who owns this wallet is completing a transaction.we are going to take a look at them later. 
A private key:Associated with each public key is a thing called “prvate key” so what a private key does is it puts signatures on all the transactions. So think of it this way we need public key to actually sign into the blockchain, once we sign in people would be able to see it using your public. But they cannot sign stuff on your behalf.so only you can do the signature using the private key. YOU DO NOT share it with anyone, hence you can write/sign but everyone can verify. Obviously this is just the skim of it however what you really to need to know is the your Private key should be left PRIVATE and your public key PUBLIC.

How to create Private and Public Keys:
We can create these keys through a verify of ways and via a lot of tools but for this specific blog we are going to use a wallet.  A wallet is essentially what allows you to take care of your private and public keys. There are alot of Ewallets out there but again for this specific blog we are going to use a popular one called “Metamask” . ethereum has a list of suggested wallets and this is one of them. We need this whole setup of the block chain on our local machine and the local system would be called a node. Think of it as the mirror of the actual blockchain you are going to be working with. Inorder to create this local node, there are plenty of tutorials that allow you to build this thing from scratch, but think of it in this way like you dont build your own webservers to start a website , you use apache etc.(layman) We are going to be using a framework called hardhat. It is a very popular tool to create local blockchain, then we are goingt to move on to a distributed global network that is going to be the ropsten test that is going to be exactly a mirror of the ethereum blockchain. And all the real life ethereum smart contracts and everything live on it the same as the actual live blockchain.It is the mirror of the mainet. It allows you to use fake currency before going to real work currency and actually deploying it on the mainet. We will not include that part unfortunately in this tutorial because that would require use of real ethereum. Once you get to the real ropsten testnet the ethereum mainnet  is literally the same thing. You just have to change a couple of URLS here and there and Boom you good to go. Essentially this is all you worry about. 



When you're going to write to the blockchain you need something which is called “Gas”, It is something mandatory inorder to write something to the blockchain. And you're going to need it for your first transaction. There are a couple of third party resources that give you the “money to play with “ on the testnet. Disclaimer this is fake money so you can't really use it to buy porn.we mean project resources.//so we are going use faucet to it some gas// finally when we are going to read some information of the blockchain, we are going to use node js application that is going to go and read the information for us, for this we are going to use the popular library called ether to communicate with the blockchain.You may have realized that we have not dug deep into the usual topics such as what blocks, hashes etc are. And the reason is that you dont need to know all of that inorder to create a blockchain and to use it.That is one of the biggest problems that make other blogs  BORING and lengthy. You dont need to know how the engine works inorder to drive a car, just like in this case you dont need to know about the hashes and the th blocks to run a blockchain. Dont take my word for it, just headover to the ethereum guy’s solidarity official documentation.(solidarity: official language for ethereum blockchain).
Sheeesh that was long.To summarize what we would be doing in this blog is that:
Make a simple Node js application 
Connect it to the blockchain
Using metamask we are going to create public private keys 
We are going to create a node with hardhat, which is going to put everything come together. 
“So letssssss get it STARTED in here”

POST 2



