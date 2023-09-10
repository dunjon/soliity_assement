# soliity_assement
This repo contains the code for the solidity beginner assignment from the metacrafters, where we have to use mint, burn and other functions and variables to create a smart contract.

# Discription
This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. The contract has different types of variables and functions by which you can mint and burn some of your tokens. This program serves as a simple and straightforward introduction to Solidity programming, and can be used as a stepping stone for more complex projects in the future.

# Getting Started 
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Copy and paste the following code into the file:

      //SPDX-License-Identifier: MIT
      
      pragma solidity ^0.8.8;
      
      contract NewToken {
          string public tokenName;
          string public tokenSymbol;
          uint256 public totalSupply;
      
          mapping(address => uint256) public balances;
      
          constructor(string memory _name, string memory _symbol, uint256 _totalSupply) {
              tokenName= _name;
             tokenSymbol = _symbol;
              totalSupply = _totalSupply;
              balances[msg.sender] = _totalSupply;
          }
      
          function mint(address _to, uint256 _value) public {
              totalSupply += _value;
              balances[_to] += _value;
          }
      
          function burn(address _from, uint256 _value) public {
              require(balances[_from] >= _value, "Insufficient balance");
              totalSupply -= _value;
              balances[_from] -= _value;
          }
      }
