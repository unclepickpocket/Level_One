
<h1>POST 1</h1>

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

<h1>POST 2</h1>

<h2>Environment Setup</h2>
Here's the stuff we'll need
NVM
Node
Hardhat
MetaMask Wallet
Set up NVM first for
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash

Add the environment variables for accessing node commands.
nvm install --lts

<h2>Install MetaMask</h2>
MetaMask will manage our wallet so that we can easily view our accounts and test our DApps easily. Go ahead and install MetaMask from https://metamask.io/. I'll use Firefox but you can just as well use Chrome.
(I strongly suggest you use MetaMask for this tutorial so that you can follow along. There's a million wallets out there and it would be difficult to debug issues if you use something other than MetaMask.)
Just go ahead and create an account on MetaMask, set your password and then save the recovery keys as given in the instructions.

<h2>Setting up Hard hat</h2>
In order to test out our smart contracts, we need an environment that simulates the ethereum network locally. We will later try out our smart contract on a global testnet too.
First, set up a react app that we will use to interact with our environment.
npx create-react-app react-dapp
cd react-dapp 

Now go ahead and set up hardhat along with all its dependencies. For now, let's not go into the details of what each part does and what alternatives are available. That would only slow you down and create confusion. It's best to get a hello world done and study options afterwards.
npm install ethers hardhat @nomiclabs/hardhat-waffle \
            ethereum-waffle chai \
            @nomiclabs/hardhat-ethers

Let's create basic hardhat configs and setup.
npx hardhat 

Accept all defaults. This will create a basic sample project for us.
We need to edit the hardhat config file so that this works well with MetaMask. ChainId is a unique identifier for the blockchain.
vi hardhat.config.js

module.exports = {
  solidity: "0.8.4",
  paths: {                         // add this 
    artifacts: './src/artifacts',  // this is where our compiled contracts will go
  },
  networks: {                      // and this ... 
    hardhat: {
      chainId: 1337                // this is needed for MetaMask
    }
  }
};

Start a node using:
npx hardhat node 

And try to connect to it using MetaMask.

<h1>POST 3</h1>

Smart Contract
Once we have the environment set up, we actually need to create a basic contract. The hello world for DApps is a greeter contract that does both reading and writing to the chain.
//SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;


import "hardhat/console.sol";


contract Greeter {
  string greeting;


  constructor(string memory _greeting) {
    console.log("Deploying a Greeter with greeting:", _greeting);
    greeting = _greeting;
  }


  function greet() public view returns (string memory) {
    return greeting;
  }


  function setGreeting(string memory _greeting) public {
    console.log("Changing greeting from '%s' to '%s'", greeting, _greeting);
    greeting = _greeting;
  }
}


Our contract is in solidity. This cannot be accessed directly from our Javascript frameworks. For that, we need to "compile" it to Javscript (ABI). Think of this as a wrapper that connects to the contract and can help you call functions of the contract without having to worry about the details (marshalling etc.) yourself.
The actual command is pretty simple:
npx hardhat compile


A new file will be created in:
src/artifacts/contracts/Greeter.sol/Greeter.json


  

We will import this file when writing our react script.
  





  



  









Starting a Dummy Network and Deploying the Contract
npx hardhat node


These are test accounts created for the purpose of testing the local network. We'll use these for a while. Make sure you don't use them on actual Mainnet or even the public testnets.
Take note of the private key and address of the first test account.
Let's go ahead and import these to our MetaMask Wallet.
First, connect to the localhost network. To do this, click on the Network dropdown (top mid) of MetaMask and select localhost. Rest of the configurations are fine.
Then, Account -> Import Account. Then paste your private key (for first test account) in there. You should have 10,000 ETH in there. They're not too useful though so don't get excited. Let's call this hh-test0x account.
Let's create a new account outside of Hardhat and send it some Ether.
Go to Metamask and Account -> Create Account. Give it a useful name. I'm using recly-test0x. Keep this account safe for now. We'll be using it later on. Save the private key by going to ... menu (the dots menu), then Account Details. Click on Export Private Key. Enter the password for MetaMask and save your private key somewhere. All of these are test keys and should defnitely not be used on mainnet.
Switch to hh-test0x account and send some ether to recly-test0x. (When you do this again the next time you start this tutorial from scratch, you will get a nonce error. For that, simply go to Accounts -> Settings -> Advanced -> Reset Account.)
Note the output in console as well as ether changes in your MetaMask accounts.

<h1>POST 4 </h1>

                            
<h2>Deploying the Greeter Smart Contract </h2>

A deploy script is created for you by Hardhat automatically. Just change it to a more meaningful name.
mv scripts/sample-script.js scripts/deploy.js

Take a look at the script and then go ahead and deploy the contract. Since this is a hello world, there isn't anything we need to change.
npx hardhat run scripts/deploy.js --network localhost

We will get an output that tells us the address (or ID) of this contract.
Greeter deployed to: 0x9fE46736679d2D9a65F0992F2272dE9f3c7fa6e0

Keep track of this address. We'll need it to interact with our contract.

 

 
<h2>Accessing from React App</h2>
Use the following basic code to access the contract. We'll discuss the code in detail but for now, just put the following content in src/App.js file.
import './App.css';
import { useState } from 'react';
import { ethers } from 'ethers'   // acts like a backend for our Web3/DApp 
import Greeter from './artifacts/contracts/Greeter.sol/Greeter.json'

// Update with the contract address logged out to the CLI when it was deployed 
// !!!!!!!! Change this ..... 
const greeterAddress = "0x5FbDB2315678afecb367f032d93F642f64180aa3"

function App() {
  // store greeting in local state of react. Has nothing to do with the smart contract at the moment
  const [greeting, setGreetingValue] = useState()

  // request access to the user's account. This works regardless of the wallet you're using. 
  async function requestAccount() {
    await window.ethereum.request({ method: 'eth_requestAccounts' });
  }

  // call the smart contract, read the current greeting value
  async function fetchGreeting() {
    if (typeof window.ethereum !== 'undefined') {
      const provider = new ethers.providers.Web3Provider(window.ethereum)
      const contract = new ethers.Contract(greeterAddress, Greeter.abi, provider)
      try {
        const data = await contract.greet()
        console.log('data: ', data)
      } catch (err) {
        console.log("Error: ", err)
      }
    }    
  }

  // call the smart contract, send an update
  async function setGreeting() {
    if (!greeting) return
    if (typeof window.ethereum !== 'undefined') {
      await requestAccount()
      const provider = new ethers.providers.Web3Provider(window.ethereum);
      const signer = provider.getSigner()
      const contract = new ethers.Contract(greeterAddress, Greeter.abi, signer)
      const transaction = await contract.setGreeting(greeting)
      await transaction.wait()
      fetchGreeting()
    }
  }

  return (
    <div className="App">
      <header className="App-header">
        <button onClick={fetchGreeting}>Fetch Greeting</button>
        <button onClick={setGreeting}>Set Greeting</button>
        <input onChange={e => setGreetingValue(e.target.value)} placeholder="Set greeting" />
      </header>
    </div>
  );
}

export default App;

Go ahead and start the npm test server on your local machine. This will let us interact with out contract through a web frontend.
npm start

The app should open in your browser.
Open Developer console and then click on the Get Greeting button. Take a look at the console where hardhat will output transaction/read details for you.
Then, enter some text in the textbox and click on Set Greeting. You should get a popup in MetaMask asking you to select an account. Select the account you have balance in and connect. MetaMask will show you the gas required to run this transaction. Click ahead to run the transaction.
See the console for hardhat that looks like this:
eth_sendRawTransaction
  Contract call:       Greeter#setGreeting
  Transaction:         0xf69ac559e520e58f5e647820a3a14cbd1f18861a8bc1b71911dfbb2da8e33a78
  From:                0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266
  To:                  0x5fbdb2315678afecb367f032d93f642f64180aa3
  Value:               0 ETH
  Gas used:            35330 of 35606
  Block #2:            0x098e048300fe12ae0812dd7c067bd274bd848481f57bcbbd94153f0b3b366636

  console.log:
    Changing greeting from 'Hello, Hardhat!' to 'New Greeting!'





Again, if you are re-doing the tutorial, reset the account in MetaMask to get rid of the stale state information in MetaMask.




