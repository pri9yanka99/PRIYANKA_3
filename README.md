# MODULE 3 PROJECT

This Solidity program is a Module 3  Project program that demonstrates the basic syntax and functionality of the Solidity programming language.
## Description

This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. The purpose of this program is to create your own ERC20 token and deploy it using REMIX . The contract has one modifier , one constructor amd two functions . In this , modifier is used for assuring that only contract owner can access the constructor and mint the tokens . The contract owner should be able to mint tokens to a provided address and any user should be able to burn and transfer tokens. Constructor is used to mint the tokens by the contract owner and functions are used to burn and transfer tokens . This program serves as a simple and straightforward introduction to Solidity programming, and can be used as a stepping stone for more complex projects in the future.

## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a.sol extension (e.g., project.sol). Copy and paste the following code into the file:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.13;

import "ERC20.sol";

contract Mtoken is ERC20 {
    address owner = msg.sender;
    modifier onlyOwner { 
        require (owner == msg.sender, "only owner can access");
        _;
    }
    constructor(string memory name, string memory symbol) ERC20(name, symbol) onlyOwner{
        // Mint 100 tokens to msg.sender
        // Similar to how
        // 1 dollar = 100 cents
        // 1 token = 1 * (10 ** decimals)
        _mint(msg.sender, 100 * 10**uint(decimals()));
    }
    function token_transfer(address add,uint256 value) external  {
        _transfer(msg.sender, add, value);
    }
    function token_burn(address add, uint256 value) external {
        burn(add, value);
    }
}

```
Then also add Context.sol , IERC20.sol and ERC20.sol files given in github, without this program cannot compile and deploy .  
To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.26" (or another compatible version), and then click on the "Compile project.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "Mtoken - project.sol" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling all the functions. 

## Author

GAURAV GARG
STUDENT
CHANDIGARH UNIVERSITY
