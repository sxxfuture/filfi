# FilFi - free your filecoin assets

An permissionless liquid market for filecoin.  Collateral your nodes and get FILs.


## Background

Building Filecoin nodes requires a large amount of pledging, which has become one of the bottlenecks in the growth of the Filecoin network, and the FIL lending market has been created to a certain extent. The built nodes themselves have a lot of value, including pledged FILs, future rewards, and linear vesting, making them ideal collateral. 

The FilFi protocol expects to release the liquidity of the nodes by collateral their Filecoin assets, lowering the financial barrier for small and medium storage providers to enter this market and adding momentum to the growth of the Filecoin network.

With the upcoming launch of the FVM, which opens up the space for a collateralized lending market, we now have the opportunity to use smart contracts and market-based mechanisms to complete the performance process in a secure and trustworthy manner, with investors contributing liquidity and node-owning builders gaining momentum for continued growth.

The goal of the Filfi project is to create a permissionless liquidity marketplace for the Filecoin community, help small and medium-sized storage providers enter the network, and facilitate the expansion and decentralization of power in the Filecoin network.


## Usecase

- Storage providers need large amounts FIL for pledging when expanding scale, and get the required FILs by collateral existing nodes.
- People who hold FILs and do not want to sell need a safe and secure way to invest.
- Everyone want to freely participates in a permissionless bilateral market that prices liquidity in a market-based manner.


## Problem

- The core problem of existing collateralized lending market is performance. Lending based on the trust of acquaintances and personal integrity can be fragile and unstable when risk occurs.
- Delivering the owner's private key just for lending is not feasible in practice.
- Both lenders and borrowers want to have free access to the liquid market.
- How can liquidity be priced in a market-based manner?
- The value of the nodes is compounded, including pledged FILs, future reward, linear vesting, which part is pledged and how much？ all requiring very flexible lending options.
- How to handle future reward as the collateraled nodes continue to reward FILs?
- How smart contracts liquidate assets independently？


# Solution

- Based on the FIP-0029 proposal, on-chain collateralization of nodes is achieved by adding smart contracts to node beneficiaries, which is the basis for trusted performance.
- By creating a collateralized lending marketplace, allowing anyone to join the marketplace without permission and free aggregation
- Supports both autonomous pricing and market pricing mechanisms to accommodate various lending scenarios.
- Maximize automated clearing through smart contracts based on the FIP-0044 proposal
- Enables cross-chain asset lending through cooperation with cross-chain projects in the FIL ecosystem

## Actors

### Borrower
- A party that provides FIL liquidity, which anyone can join freely without permission.
- Receives revenue by lending fil. (Can be extended to support other on-chain assets of Filecoin)
- Lending can be: 1. directional lending, 2. fixed price lending 3. interest-bearing savings
- When the lender defaults, the smart contract automatically liquidates the collateral and repays the borrower's assets.

### Lender
  - The party borrowing from FIL obtains liquid FIL by pledging node assets.
  - Assets that can be pledged by a node include
    - Pledged coins
    - Future earnings (liquid portion and locked portion)
  - Costs to be deducted
    - Gas fee

### Data feed

- Decentralized information input architecture
- Supports data input from the real world to the blockchain (when supporting cross-chain assets, the market price of the assets needs to be monitored through this system)

### DAO 

- DAO is made up of individuals and service providers that offer specific services to DAOs through governance tokens and governance processes.
- Members are independent market participants, not employed.
- Members are divided into different roles. For example, the Governance Coordinator, who chairs the communication and governance process; and members of the Risk Team, who support Filfi governance through financial risk research and drafting proposals for the introduction of new types of collateral and the management of existing collateral.

## Interacting with Filfil

### Lenders

1. **Create an asset package and configure a collateral plan.**
Login to Filfi's DApp using your personal wallet, create an asset package, and follow the prompts to the next step.
2. **Go back to the Filcoin node to complete the collateral operation.**
Change the node beneficiary to the smart contract address generated in the previous step, and complete the confirmation in the DApp.
3. **Configure the collateral scheme and determine the final locked assets.**
Lock the assets to be collateralized in the DApp. Only locked assets will be involved when liquidation occurs, unlocked assets will always be safe.
4. **If choose to borrowing from the open market.**
View the open market lending price given by DApp, if accepted, FIL will be transferred to the specified account immediately.
5. **If choose to borrowing from other peer.**
Fill in the borrowing price and send the link to the borrower. After the borrower completes the operation, FIL will be transferred to the specified account immediately.
6. **Repay the debt.**
Login to Filfi's DApp using your personal wallet and repay the debt.
7. **Go back to Filecoin node to cancel the collateral.**
Remove the smart contract from the beneficiary and complete the confirmation in the DApp (or the smart contract checks automatically) and the asset will be automatically transferred to the debitor's account.

### Borrowers 

1. **Browse Debit Contracts.**
Login to Filfil's DApp using your personal wallet to view the details of debit and credit contracts issued by the borrower.
2. **Put in fil.**
Sign your personal wallet to invest FIL into the smart contract.
3. **View assets at any time.**
Log in to Filfil's DApp using your personal wallet to view the status of your assets at any time.
4. **When a lender makes a repayment, the assets are automatically transferred to the designated account.**


## Smart Contracts Module

### Asset Package Module
The Asset Package module holds the basic building blocks of the Filfi protocol.
- Database - risk parameters as well as collateral and debt balances.
- Accounting System - Basic accounting operations for updating the database.
- Asset Package Management - Adjusts locked collateral and debt positions.
- Asset package flow - the ability to transfer, split and consolidate asset packages
These building blocks of asset packages are designed not to be upgraded or replaced.

### Collateral Module
Collateralization of Filecoin nodes requires multiple steps to complete, and the Collateral Module manages the entire process.
- Add Collateral - Collateralizes the node to the asset package.
- Locking collateral - locks part of the node's assets.

### Liquidation Module
When a default condition occurs, the liquidation module will do the liquidation of the asset package, which includes two ways.
- Termination Node - Recover all assets through the Termination Node
- Debt Auction - recovering the assets by auction in case it is not possible to terminate the node.
Liquidation is based on two principles
- Maximizing coverage of the debt
- Maximizing the return to the collateral owner

### Messenger Module
When supporting cross-chain assets, the Filfi protocol requires real-time information about the market price of the assets used as collateral in the asset package. Ultimately, this market price determines the terms of liquidation. The Oracle module handles how the market price is recorded on the blockchain.
The messenger module is an interface contract where external actors extract the current market price for a given collateral type from the price prognosticator module.

### Governance Module
The Governance module contains, tokens and contracts for authorization, voting, proposal execution and voting security.

# Products
Filfil - An permissionless liquid market for filecoin
- Web version: HTML5 page version, login via wallet
- Mobile version: installed on cell phones, not connected to any centralized server

# Roadmap
