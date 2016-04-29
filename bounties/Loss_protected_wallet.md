![alt text](https://github.com/bitDubai/media-kit/blob/master/MediaKit/Fermat%20Branding/Fermat%20Logotype/Fermat_Logo_3D.png "Fermat Logo")

# Loss Protected Wallet

## Introduction

Its main goal is to protect the user from losing money when attempting to spend Bitcoins at a price lower than the price when that Bitcoin amount was first purchased (or entered the wallet).
The new functionalities include:
* Storing the exchange rate when a BTC amount is received in the wallet
* Checking the exchange rate when the user attempts to spend an amount of BTC and freeze the funds if they are below the purchased price

When spending the BTC the app will evaluate if the exchange rate at that moment is higher than the last saved exchange rate in the wallet, and it will allow to start spending the value blocks, starting first with the value block with the highest exchange rate to then consume the following value blocks with lower exchange rate.

The Fermat book chapter related to this bounty can be found here: https://github.com/Fermat-ORG/fermat-book/blob/master/book-chapter-12.asciidoc

## Scope

## General Purpose

Develop the Loss Protected Wallet app that will be part of the CCP layer and will reutilize components already made like Network Services, transactional modules and contact modules.

It will have the same functionalities as the Bitcoin Wallet and the following functionalities will be added as well to this wallet:
* The balance available will be estimated based on the value blocks that it can consume at the moment regarding the BTC exchange rate in dollars.

* Show in a screen the BTC available in the wallet and how much has been consumed from each chunk value.

* When making a payment you will not be able to exceed the balance available estimated based on the current dollar exchange rate.

* The current BTC exchange rate in dollars will be shown.

* From the wallet settings you’ll be able to avoid the BTC loss protection restriction by selecting a setting in the wallet configuration. If it is on true it will not allow the spending the BTC and if it is on false it will allow the spending the BTC.

 For this new wallet we will need to develop the following components:
 
 - Loss Protected Wallet App
 - Loss Protected Wallet Module
 - Basic Loss Protected Wallet
 - Transactional module of BTC exchange intra device

### Current developments in progress

This wallet will reutilize the CCP components already developed
- Transactional module of Incoming and Outgoing
- Contacts plug-ins
- Network Services for sending metadata.
- Network Services for connections between Fermat Intra Actors
- Network Services for obtaining Intra Actors address
- Network Services for sending and receiving Payment Request.
- Crypto address module.
- Payment request module.

The Community subapp will be used to establish relations between Fermat Users, which will then be able to be added as contacts, and the Identity subapp to create de identity associated to the wallet. 

The current dollar exchange rate is obtained from the Crypto World Fiat Index CBP component


### Bounty scope

#### Objectives to accomplish 
The following components will be developed:
 * App Loss Protected Wallet: android application that will allow the user to use the functions of the wallet.
 * Module Loss Protected Wallet: will connect the Android app with the rest of the plug-ins.
 * Basic Loss Protected Wallet: plug-in that will save the information of the wallet transactions, balance and exchange rate.
 * Develop a transactional BTC exchange module intra wallets.
 * Develop the functionality that allows taking each BTC from the wallet as a unit that will divide off, if necessary, to start consuming them based on the evaluation of the original exchange they had when they were deposited and the exchange when they were consumed.

#### Workflows

**Sending BTC**: The wallet user selects the option Send, then specifies the contact he wants to send the BTC to and the amount, then presses Send. The balance available is verified to spend based on the current dollar exchange rate in contrast to the original exchange rate of the different BTC received.
If the exchange is lower the user will be informed that he will not be able to send the money or he will lose it, if the bypass restriction setting is on then the user will be able to send the money despite the warning. Otherwise it will not be done.

  If the exchange is higher the transaction is sent through the transactional CCP Outgoing Intra Actor Transaction module, or from the CCP Outgoing Extra Actor Transaction for external contacts, to the Crypto Vault module and the BTC are sent through the Crypto Bitcoin Network module. 

  The amount sent is deducted from the wallet balance through the Loss Protected Basic Wallet module that registers the transaction. An estimate is made of how many value blocks were consumed in this transaction and the balance available is updated.

  The Network Services Crypto Transmission sends the metadata with the transaction information through the Fermat P2P server.

**Receiving BTC**: The Crypto Bitcoin Network module informs the Incoming Intra User Transaction module, or the CCP Incoming Extra Actor Transaction module for external contacts, that a new transaction arrived to this wallet.
The Network Services Crypto Transmission waits for the arrival of the metadata to apply the transaction through the Loss Protected Basic Wallet module that then registers the transaction and searches for the current BTC exchange rate in dollars, to then save that information and update the balance available.

**Add a connection with an Intra User as a contact**: From the wallet contact option you will be able to add a new Fermat User type contact, when choosing this option you will see a list of connections already made through the Community subapp, if you don’t have any connections you will be able to access the Community subapp to make them.
When selecting one of these Fermat Users from the list a new contact will be created for the wallet through the Wallet Contact Middleware module and the contact wallet address will be solicited through the Network Services Crypto Address which sends a request to the other device by means of the Fermat P2P network for the address to return.

**Sending or Receiving a payment Request**: From the contact details or from the payment request screen you can access the form to make a new payment request, you select the contact and the amount of BTC requested when pressing Send the request is then saved by the Crypto Payment Request module and it informs the Network Services Crypto Payment Request to send the payment request to the device wanted through the Fermat P2P network.
When the other device receives the payment request it responds by confirming it received it.

When receiving a payment request the Network Services Crypto Payment Request send an event to the Crypto Payment Request module to notify it that a new request was received that way the module registers it and then it is shown on the Payment Request Received list of the wallet.

**Deny a Payment Request**: When receiving a new payment request from the Payment Request Received list you select the option Deny, at the Crypto Payment Request module the status of the request is then changed to denied and the Network Services Crypto Payment Request is informed that it should send a notification to the other device that the request was denied by means of the Fermat P2P network.

**Accept a Payment Request**: When receiving a new payment request from the Payment Request Received list you select the option Accept, the described flow runs in order to send the BTC and once the transaction is made it is then changed in the Crypto Payment Request module the request status to accepted and the Network Services Crypto Payment Request is informed that it should send a notification to the other device that the request was accepted by means of the Fermat P2P network.


**Make a transfer to another wallet**: From this wallet you will be able to do a BTC transfer to another wallet of the Fermat platform owned by the user. The user enters another wallet to the BTC transfer screen, selects the wallet and the amount of BTC to transfer, (this option will not have protection restrictions) then presses Send.
The transaction is sent to the Crypto Vault module through the Outgoing Device User Transaction module to the Crypto Vault module and the BTC are sent through the Crypto Bitcoin Network module. 
 The balance amount sent is deducted from the wallet through the Loss Protected Basic Wallet module which registers the transaction. And an estimate is made of how many value blocks were consumed in this transaction and then the balance available is updated.
  The metadata is sent through the NetWork Services Crytpo Transmission with the transaction information by means of the Fermat P2P server.


#### Wallet Graphic interface
- Home:
      * Summary of the balance available and book
      * List of transactions sent and received
- Navigation Drawer: 
       * Identity: allows going to the Identity subapp and modifying the data brought up, like User Name and photo.
       * Contacts
          * List of Contacts
          * View contact details with the option of making a payment request or sending BTC.
          * Add a new external contact or a Fermat User.
       * Payment Request
          * List of Requests sent and received
          * Make a new payment request
       * Statistics of consumption of value blocks
       * Settings
           * Send BTC to another wallet
           * Enabled Send BTC Protected
           * Change Networks
- Wallet Toolbar
       * Help
       * Send BTC to contacts
       
    

## Timeline

Based on the workload and the resources available currently, the delivery date for this reward (bounty) will be **April 15th**.

## Evaluation

To be considered successful this reward (bounty) must surpass the following:

* All the elements previously exposed must be made.

* An evaluation will be done based on what was done by each of the developers. A mathematical estimate will be made to determine what that person contributed in order to complete the bounty based on the amount of elements successfully made.

*[Evaluation results to be completed after evaluation]*

## Distribution

*[Distribution to be completed after evaluation]*

