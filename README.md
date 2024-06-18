# MyBank Smart Contract

The "MyBank" project involves the deployment of a smart contract on the Ethereum blockchain that acts as a simple bank. It includes functionalities for depositing and withdrawing funds, transferring funds to other addresses, and performing basic assertions and reverts for testing purposes.

## Description

The "MyBank" smart contract is designed to manage a basic bank account on the Ethereum blockchain. It allows the contract owner to deposit and withdraw funds, transfer funds to other addresses, and includes assertion and revert functions for testing conditions within the contract.

## Getting Started

### Prerequisites

To interact with this smart contract, you will need:

- An Ethereum wallet (such as MetaMask)
- Some test ETH to deploy and interact with the contract (available from testnet faucets)
- Remix IDE or another Solidity development environment

### Executing Program

To run this program, you can use Remix, an online Solidity IDE. Follow these steps to get started:

1. Go to the Remix website at [https://remix.ethereum.org/](https://remix.ethereum.org/).

2. Create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., MyBank.sol).

3. Copy and paste the following code into the file:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MyBank {
    address private owner;
    uint public balance;

    constructor() {
        owner = msg.sender;
        balance = 0;
    }

    function deposit(uint amount) public {
        require(amount > 0, "add amount");
        balance += amount;
    }

    function withdraw(uint amount) public {
        require(msg.sender == owner, "owner can withdraw");
        require(amount <= balance, "balance not sufficient");
        balance -= amount;
    }

    function transfer(address payable recipient, uint amount) public {
        require(recipient != address(0), "can't transfer");
        require(msg.sender == owner, "owner can transfer");
        require(amount <= balance, "balance not sufficient");
        balance -= amount;
        recipient.transfer(amount);
    }

    function Assert() public pure {
        uint x = 5;
        assert(x == 5);
        x = 10;
        assert(x == 5);
    }

    function Revert() public pure {
        revert("this will never revert");
    }
}
```

4. To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.0" (or another compatible version), and then click on the "Compile MyBank.sol" button.

5. Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "MyBank" contract from the dropdown menu, and then click on the "Deploy" button.

## Usage

After deploying the contract, you can interact with its functions:

- **deposit(uint amount)**: Allows any user to deposit a specified amount of funds into the contract.
- **withdraw(uint amount)**: Allows the owner to withdraw a specified amount of funds from the contract.
- **transfer(address payable recipient, uint amount)**: Allows the owner to transfer a specified amount of funds to another address.
- **Assert()**: A test function that uses the assert statement to check conditions.
- **Revert()**: A test function that always reverts with an error message.

## Authors

Kashni  
[kashniarora@gmail.com](mailto:kashniarora@gmail.com)
