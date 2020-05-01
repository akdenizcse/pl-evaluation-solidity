# pl-evaluation-solidity

  
  ![logo](https://user-images.githubusercontent.com/62035132/80819105-08ce6a00-8bdd-11ea-84b3-0f01b9a35ccc.png)

  
 -------------------------------------------
  ### Authors & History
  
  Briefly `Solidity` development in three different stages
  
 - August 2014: The Solidity language is proposed by Gavin Wood
 - October 2014: Solidity is adopted as a language by Monax, a rival platform.
 -  August 2015: Solidity is officially released.

 
Explanation about the history and authors of `Solidity` .
-  Solidity is a high-level, human-readable code that breaks it down into specific instructions that are easily understandable for machines. The main advantages of using Solidity include:
- Solidity was first proposed by Gavin Wood in August 2014, but the language was later developed by the Ethereum team.
Ethereum team includes  Christian Reitwiessner, Alex Beregszaszi, Yoichi Hirai and several former Ethereum core
Solidity is an object-oriented programming language for writing smart contracts.
It is used for implementing smart contracts on various blockchain platforms, most notably,Ethereum.
- Contributors to enable writing smart contracts on blockchain platforms such as Ethereum.
-  Solidity includes targeting Ethereum Virtual Machine (ESM) from C ++, Python and JavaScript.
-  Solidity is written statically. It supports inter-object heritage relationship, libraries and user-defined complex types, among other things.

---------------------

### Why Solidity was  invented

It is an object oriented, high level programming language developed for the implementation of smart contracts.
Smart contracts are programs that manage the behavior of transactions on the Ethereum network.

------------------
### When/why shall we use Solidity
- WHEN?.

With this language, you can write smart contracts, voting, crowdfunding, auction and multi-signature wallets.

- WHY?.

Advantages of Solidity in Developing Smart Contracts in Blockchain Applications.

  1-Solidity provides object-oriented programming attributes in contracts including multiple level inheritance properties.
  
  2-Solidity developed for Contracts maintains multiple members of variables in order to represent and arrangements.
  
  3-Multiple types of supporting roles are also carried in Solidity through the expediting Application Binary Interface.
  
  4-Using contracts fundraising can be done and can provide solutions for various problems raised like third-party expenses and reduce the cost of managing data.
  
  5-Solidity has a similar syntax to JavaScript and C++ that makes it easier to learn Blockchain development basics for those with respective skills. The same source code for Solidity can be written in C++ too.
  
-------------------------------
### How to setup an environment to use it in different platforms (windows, mac, linux)
 
-  Step 1 npm / Node.js

Use npm for a convenient and portable way to install solcjs, a Solidity compiler.
This download link contains windows, mac,linux etc. versions .
https://nodejs.org/en/download/

-  Step 2  Programming Language

 We need a programming language that compile our smart contract into bytecode that the Ethereum virtual machine can understand. There are different options but by far the most popular is a solidity.
  `npm install -g solc`
 - Step 3 Docker
 
We provide up to date docker builds for the compiler. The stable repository contains released versions while the nightly repository contains potentially unstable changes in the develop branch.
 `docker run ethereum/solc:stable solc --version`
 - Step 4 Binary Packages
 
 Currently, the docker image only contains the compiler executable, so you have to do some additional work to link in the source and output directories.
https://github.com/ethereum/solidity/releases (This download link contains windows, mac,linux etc. versions )
  
  -  Remix (DOWNLOAD WITHOUT ANYTHING YOU CAN START LEARNING)
   
We recommend Remix for small contracts and for quickly learning Solidity.
Access Remix online, you don’t need to install anything. If you want to use it without connection to the Internet, go to https://github.com/ethereum/browser-solidity/tree/gh-pages and download the .ZIP file as explained on that page.


----------------------------------
### Examples
 #### SmartContract example
- what does exactly that smart contract example do? .

This code gives value one variable and try to access this variable with another contract.

```
pragma solidity >=0.4.0 <0.7.0;
  
contract SimpleStorage {
    uint storedData;

    function set(uint x) public {
        storedData = x;
    }

    function get() public view returns (uint) {
        return storedData;
    }
}'
```
Explanation of this `Simple smart contract`  line by line
-  The first line simply says that the source code is written for Solidity version 0.4.0 or a newer version that does not disrupt functionality (does not include those up to version 0.6.0).This is used to ensure that the contract may behave differently or be corrupted, not compatible with a new (compiler) version of the compiler.
- The uint storedData line defines a status variable named storedDate of unit type (256 bit integer). You can think of this as a database information that can be cooled and replaced with the functions used in the contract. When it comes to Ethereum, this is always a contract of ownership. And in this case, the set and get functions can be used to change the value of the variable or to call the variable.

- General meaning of this Smart Contract;
Due to the infrastructure created by Ethereum, this contract has no function other than providing anyone access to this variable you assign on Earth. Of course, anyone can publish a contract that contains a variable that is equal to a different value like this, or want to change the value of your variable, but your contract and variable value are stored in the blockchain along with its date. Next, we will see how you can implement access restrictions so that only you can change your own variable.
--------------------------
#### Coin example

- what does exactly that Coin example do?.

The evaluation agreement is written in the simplest way to create a cryptocurrency. It is possible to generate cryptocurrencies with Ethereum smart contracts, but only the creator can do it. Anyone on the network can send and receive money without needing to register somewhere - the only thing you need is  an Ethereum key pair.

```
pragma solidity ^0.5.0;

contract Coin {
   
    address public minter;
    mapping (address => uint) public balances;
    event Sent(address from, address to, uint amount);

    constructor() public {
        minter = msg.sender;
    }

    function mint(address receiver, uint amount) public {
        require(msg.sender == minter);
        require(amount < 1e60);
        balances[receiver] += amount;
    }

    function send(address receiver, uint amount) public {
        require(amount <= balances[msg.sender], "Insufficient balance.");
        balances[msg.sender] -= amount;
        balances[receiver] += amount;
        emit Sent(msg.sender, receiver, amount);
    }
}
```
Explanation of this ` Coin`  line by line
 First of all this contract introduces some new concepts,let's check new concepts one by one.
- ```Address public minter;``` The line declares a generally accessible address type status variable. The address type is a 160-bit value that does not allow arithmetic operations. This type is suitable for storing their contractual addresses or key pairs of external persons. The public keyword has a function that allows the current value of the status variable to be accessed from outside the contract. Access to this variable from other contracts is not allowed if this keyword is not used.
- ``` mapping (address => uint) public balances;``` also creates a public state variable, but it is a more complex datatype. The type maps addresses to unsigned integers. Mappings can be seen as hash tables which are virtually initialized such that every possible key exists and is mapped to a value whose byte-representation is all zeros.

- ```event Sent(address from, address to, uint amount;``` declares a so-called “event” which is emitted in the last line of the function send. User interfaces (as well as server applications of course) can listen for those events being emitted on the blockchain without much cost. As soon as it is emitted, the listener will also receive the arguments from, to and amount, which makes it easy to track transactions.To listen to this event, you need to use the following JavaScript code (Here it is assumed that Coin is a contract object created via web3.js or similar module):

 
 ```
  
  Coin.Sent().watch({}, '', function(error, result) {
  if (!error) {
        console.log("Coin transfer: " + result.args.amount +
            " coins were sent from " + result.args.from +
            " to " + result.args.to + ".");
        console.log("Balances now:\n" +
            "Sender: " + Coin.balances.call(result.args.from) +
            "Receiver: " + Coin.balances.call(result.args.to));
    }
})

 ```
 The Constructer function ''Coin'' is a special function that is specified only during the creation of the contract and cannot be called later. It permanently stores the address of the contract creator: msg (with tx and block) is a special global variable that contains some features that allow access to the blockchain. msg.sender is always the address where a valid (external) function call comes.


Finally, the functions that can be specified at the end of the contract and then called by users and other contracts are the mint and send functions. If the mint function is called by anyone other than the contractor, it will not cause any changes. This is guaranteed by a special function that rejects any changes if the argument require require is false. The second require call is to prevent too much money to cause overflow errors later.

On the other hand, sending money to anyone else on the network can be used by anyone who already has this cryptocurrency. If there is not enough money to be sent, the require call will fail and an appropriate error message will be sent to the user.
 
 
 `mert karababa 20160807017` 
