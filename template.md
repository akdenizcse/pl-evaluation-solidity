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
- this example is one of the `smart contract` but simple one. 
- what does exactly that smart contract example do? ss.

That sets the value of a variable and exposes it for other contracts to access.

```pragma solidity >=0.4.0 <0.7.0;

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
Explanation of this `Simple smart contract` 
-  The first line simply says that the source code is written for Solidity version 0.4.0 or a newer version that does not disrupt functionality (does not include those up to version 0.6.0).








 `mert karababa 20160807017` 
