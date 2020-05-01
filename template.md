# pl-evaluation-solidity

  
  ![logo](https://user-images.githubusercontent.com/62035132/80819105-08ce6a00-8bdd-11ea-84b3-0f01b9a35ccc.png)

  
 -------------------------------------------
  ### Authors & History
  
  Briefly `Solidity` development in three different stages
  
 - August 2014: The Solidity language is proposed by Gavin Wood
 - October 2014: Solidity is adopted as a language by Monax, a rival platform.
 -  August 2015: Solidity is officially released.
 ------------------
 
Explanation about the history and authors of `Solidity` .
 
- Solidity was first proposed by Gavin Wood in August 2014, but the language was later developed by the Ethereum team.
Ethereum team includes  Christian Reitwiessner, Alex Beregszaszi, Yoichi Hirai and several former Ethereum core
Solidity is an object-oriented programming language for writing smart contracts.
It is used for implementing smart contracts on various blockchain platforms, most notably,Ethereum.
- Contributors to enable writing smart contracts on blockchain platforms such as Ethereum.
-  Solidity includes targeting Ethereum Virtual Machine (ESM) from C ++, Python and JavaScript.
-  Solidity is written statically. It supports inter-object heritage relationship, libraries and user-defined complex types, among other things.
---------------------
#### Why Solidity invented
------------------------
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
------------------------
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

- ```event Sent(address from, address to, uint amount;``` declares a so-called “event” which is emitted in the last line of the function send. User interfaces (as well as server applications of course) can listen for those events being emitted on the blockchain without much cost. As soon as it is emitted, the listener will also receive the arguments from, to and amount, which makes it easy to track transactions. In order to listen for this event, you would use

 `mert karababa 20160807017` 
