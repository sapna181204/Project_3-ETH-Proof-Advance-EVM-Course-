# Project_2-ETH-Proof-Advance-EVM-Course-
# ETH Proof: Advance EVM Course


# Corrected Code

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;                                       //corrected license

contract StorageVictim {
    address owner;                                            //stores owner's address

    struct Storage {                                          //Defines a new data type 'Storage' as a struct
        address user;                                         //stores user's address
        uint amount;                                          //stores amount of user 
    }

    mapping(address => Storage) storages;                     //mapping to store 'Storage' structs for different addresses

    constructor() {                                           //constructor created instead of function
        owner = msg.sender;                                   //sets owner to address
    }

    function store(uint _amount) public {                     //arguments given and function to store user's amount
        Storage storage str = storages[msg.sender];           //reference to the storage location of the 'Storage'
        str.user = msg.sender;                                //sets user's field to caller's address
        str.amount = _amount;                                 //sets amount field to provided amount
    }

    function getStore() public view returns (address, uint) { //function that retrieves user's amount
        Storage storage str = storages[msg.sender];           //creates storage reference for caller's address
        return (str.user, str.amount);                        //returns user and amount to 'Storage'
    }

    function getOwner() public view returns (address) {       //function to retrieve owner's address
        return owner;                                         //returns the address
    }
}

# README.txt 
REMIX DEFAULT WORKSPACE

Remix default workspace is present when:
i. Remix loads for the very first time 
ii. A new workspace is created with 'Default' template
iii. There are no files existing in the File Explorer

This workspace contains 3 directories:

1. 'contracts': Holds three contracts with increasing levels of complexity.
2. 'scripts': Contains four typescript files to deploy a contract. It is explained below.
3. 'tests': Contains one Solidity test file for 'Ballot' contract & one JS test file for 'Storage' contract.

SCRIPTS

The 'scripts' folder has four typescript files which help to deploy the 'Storage' contract using 'web3.js' and 'ethers.js' libraries.

For the deployment of any other contract, just update the contract's name from 'Storage' to the desired contract and provide constructor arguments accordingly 
in the file `deploy_with_ethers.ts` or  `deploy_with_web3.ts`

In the 'tests' folder there is a script containing Mocha-Chai unit tests for 'Storage' contract.

To run a script, right click on file name in the file explorer and click 'Run'. Remember, Solidity file must already be compiled.
Output from script will appear in remix terminal.

Please note, require/import is supported in a limited manner for Remix supported modules.
For now, modules supported by Remix are ethers, web3, swarmgw, chai, multihashes, remix and hardhat only for hardhat.ethers object/plugin.
For unsupported modules, an error like this will be thrown: '<module_name> module require is not supported by Remix IDE' will be shown.


