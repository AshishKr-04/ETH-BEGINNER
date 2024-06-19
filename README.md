## Introduction 
This repository contains the source code for the `MyToken` smart contract. This contract allows for the creation, mapping, minting, and burning of a custom token on the Ethereum blockchain.
## Description
This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. In this contract I create `MyToken`smart contract whose detials are

Contract Details

The `MyToken` contract includes the following public variables to store the details about the token:
- `name`: The name of the token.
- `symbol`: The abbreviation of the token.
- `totalSupply`: The total supply of the token.

Additionally, it has a mapping to store balances of addresses:
- `balances`: A mapping of addresses to their respective token balances.

Functions

- setTokenDetails

The `setTokenDetails` function initializes the token with its name, abbreviation, and initial supply. This function is meant to be called once to set up the token details.

Parameters:
- `string memory _name`: The name of the token.
- `string memory _abbrv`: The abbreviation of the token.
- `uint _initialSupply`: The initial supply of the token.

This function sets the `tokenName`, `tokenAbbrv`, and `totalSupply` variables, and assigns the initial supply to the contract deployer's address.

 - Mint

The `mint` function allows the creation of new tokens. It takes two parameters:
- `address _to`: The address of the account where tokens will be minted.
- `uint _value`: The number of tokens to mint.

The function increases the `totalSupply` by the specified amount and also increases the balance of the specified address.

- Burn
The `burn` function allows the destruction of tokens. It takes two parameters:
- `address _from`: The address of the account where tokens will be burned.
- `uint _value`: The number of tokens to burn.

The function decreases the `totalSupply` by the specified amount and also decreases the balance of the specified address. It includes a check to ensure that the balance of the account is greater than or equal to the amount to be burned. If the balance is insufficient, the transaction reverts with an error message.

## Getting Started
- Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/. 

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. 
Save the file with a .sol extension (e.g. Mycontract.sol). Copy and paste the following code into the file:

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.7;

/*
       REQUIREMENTS
    1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
    2. Your contract will have a mapping of addresses to balances (address => uint)
    3. You will have a mint function that takes two parameters: an address and a value. 
       The function then increases the total supply by that number and increases the balance 
       of the “sender” address by that amount
    4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
       It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
       and from the balance of the “sender”.
    5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
       to the amount that is supposed to be burned.
*/
## Source Code



    
    contract MyToken {
    // public variables here

    string public tokenName;
    string public tokenAbbrv;
    uint public totalSupply;
    // mapping variable here
    mapping(address => uint) public balances;
    // Function to set token details (name, abbreviation, and initial supply)
    function setTokenDetails(string memory _name, string memory _abbrv, uint _initialSupply) public {
        tokenName = _name;
        tokenAbbrv = _abbrv;
        totalSupply = _initialSupply;
        balances[msg.sender] = _initialSupply;
    }
    // mint function
    function mint(address _to, uint _value) public {
        totalSupply += _value;
        balances[_to] += _value;
    }

    // burn function
    function burn(address _from, uint _value) public {
        if (balances[_from] >= _value) {
            totalSupply -= _value;
            balances[_from] -= _value;
        } else {
            revert("Balance too low to burn");
        }
    } 
    }




To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. 

Make sure the "Compiler" option is set to "^0.8.7", and then click on the "MyToken.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. 

Select the "Mycontract" contract from the dropdown menu, and then click on the "Deploy" button.

Initialize the token details by calling the `setTokenDetails` function with the appropriate parameters:

    ```solidity
    myToken.setTokenDetails("MyToken", "MTK", 0);
    ```
    Finally, click on the "transact" button to execute the function `setTokenDetails`and retrieve the token details .

Mint new tokens to a specified address:

    ```solidity
    myToken.mint(0xAbC1234567890DeF, 100);
    ```
    click on the "transact" button to execute the function ``mint``and retrieve the token details .
Burn tokens from a specified address:
    ```solidity
    myToken.burn(0xAbC1234567890DeF, 50);
    ```

    
 click on the "transact" button to execute the function `burn` and retrieve the token details .

## License
This project is licensed under the MIT License. See the LICENSE file for details.

