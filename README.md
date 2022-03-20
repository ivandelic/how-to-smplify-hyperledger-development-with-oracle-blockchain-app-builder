# How to simplify Hyperledger development with Oracle Blockchain App Builder
What is a Blockchain? What can Oracle Blockchain offer beyond Hyperledger Fabric? How to build a production-grade blockchain network with smart contracts and test them locally? Why should you leverage DLT and smart contracts in every typical architecture? Continue reading and explore highlights of Oracle Blockchain Platform, together with a new toolset for building smart contracts - Blockchain App Builder.

You can find the following topics:
* [Introduction](#introduction)
* [Hands-On](#hands-on)

## Introduction
------

### A Blockchain
A blockchain is a system for storing data through distributed ledgers, powered by cryptography and automation. One could paraphrase it as a distributed database, but it wouldn't be fair since it's so much more. One way of looking at it might be a distributed database with a continuously growing list of irreversible records (called blocks) linked and secured using cryptography. Still, it's more than that since it contains the business logic inside (called smart contracts), enabling the automation of business processes between different organizations, in a distributed network, without any manual integrations. 

Blockchain was first introduced in 2008 as the distributed ledger behind Bitcoin and evolved in many variations. Bitcoin [manifesto](https://bitcoin.org/bitcoin.pdf) never mentioned it explicitly, but you would find many mentions of blocks and chains. The community later forged the blockchain term to describe underlying technology and techniques. Nowadays, blockchains evolved into private, public, and hybrid networks. Bitcoin and Ethereum are public permissionless blockchains, while Hyperledger Fabric implements private permissioned blockchain. A permissioned blockchain network typically has a founder that creates and maintains the network and participants that join the network. Since it's permissioned, you cannot gain access to it unless explicitly given by the founder.

### What is Hyperledger Fabric?
Hyperledger Fabric is an enterprise-grade, permissioned blockchain framework applicable to a broad set of industry use cases. It is a widely adopted open-source tool under the Linux Foundation.

Hyperledger Fabric components create a decentralized network. The network may contain multiple organizations and nodes. Each organization has a role (network founder or member) and responsibility to manage its nodes. The below diagram presents a simple network topology where the founder organization is connected with two other member organizations in a single consortium.

![Hyperledger Fabric Architecture](images/hl-architecture-1.png)

The essential Hyperledger Fabric components are Peers, Orderers and Certificate Authorities. Peers hold the log of transactions (the blockchain) and the world state (aggregated view of all transactions). Orderers maintain the consistency of the state and create blocks of transactions. Certificate Authorities connect the whole network via the certificate's chain of trust by issuing keys to selected participants.

![](images/hl-architecture-3.png)

Other substantial Fabric components are Channels and Chaincodes. Channel is a crucial abstraction in Hyperledger Fabric, ensuring privacy and isolation among network members if needed. You can consider it a concept similar to VLAN in networking, preventing other computers on the same physical network from sensing your traffic and data. Another way of looking at it might be a VM hypervisor that enables multiple VMs on a single bare-metal computer. This is what channels essentially are - isolation and privacy of members in the same physical blockchain network. All peers belonging to a channel have access to the same data and smart contracts. There is no access to it outside the channel. The below diagram describes channels and their interaction with peers. Two distinct channels (default and dev) are isolated from each other. The default channel is executed on both peers (peer0 and peer1), while the dev channel is executed only within peer0.

![Hyperledger Fabric Architecture - Channels](images/hl-architecture-2.png)

Last but not least, Hyperledger Fabric components are Chaincodes. Chaincode is smart contracts, a program, written typically in Go, TypeScript, or Java that contain the business logic to be executed as transactions on the blockchain. The true power of the chaincodes is the automation of business processes in a distributed network without any manual integration or human mistakes. Want to sell your house for money and be sure you want to be tricked? Automate the process with chaincodes. 

### How Oracle Enriched Hyperledger Fabric?
Oracle embraced Hyperledger Fabric and established Oracle Blockchain Platform (OBP). Oracle Blockchain Platform is a permissioned blockchain that provides a secure ecosystem where only invited organizations can join the network and keep a copy of the ledger. The founding organization, or blockchain network owner, determines the network participants.

Oracle Blockchain Platform is a managed blockchain solution designed to set up Hyperledger Fabric network(s). It offloads the burden of Hyperledger components maintenance, focusing you on the applications and smart contract development. Oracle Blockchain Platform provides you with all the required components to support a blockchain network: computes, storage, containers, identity services, event services, and management services. Start developing and deploying blockchain applications in minutes. Build and deploy productional systems in days or weeks rather than months.

![Menu](images/obp-architecture-1.png)

From the architectural diagram above, you can spot the added value of the Oracle Blockchain Platform in terms of REST APIs, Administrative Console, and Managed infrastructure. Rest Proxy enables fluid REST communication with Hyperledger Fabric APIs (otherwise, you need to use SDK and configure it). This significantly impacts native JavaScipt applications, removing the need to build proxy NodeJS services for accessing Hyperledger nodes. The administrative console makes the administration more manageable compared to the vanilla Hyperledger implementation. Use the user interface to manage nodes, create channels, deploy chaincodes. Managed infrastructure removes a significant maintenance burden from your back.

To make Hyperledger Fabric development more manageable, Oracle developed a toolset for rapid blockchain development - Blockchain App Builder. It comprises CLI and Visual Studio Code extensions that help develop, test, debug, and deploy smart contracts (chaincodes) on Oracle Blockchain networks.

### Why Would You Use Oracle Blockchain Platform?

Modern societies suffer from the complex bureaucracy within the citizen-to-government processes. No matter the country you are coming from, you have faced bureaucratic gaps, mismatched data, or the need to reflect your personal data in multiple distinct systems. Each country has government institutions responsible for different legal domains, such as taxes, work, health, justice, and others. Those domains are represented with the institutions such as Tax Authority, Work and Pensions Department, and Health Insurance.

The below diagram depicts citizen-to-government processes in everyday communication with Tax Authority, Work & Pensions Department, and Health insurance. Without integration between institutions, the citizen would face a lot of repetitive manual tasks of filling different papers and forms for each action you do with them.

![](images/uc-egov-1.png)

Examining the upper diagram, you can notice that the entity "Person" repeats across all three institutions. It means that, most probably, all three institutions are owners of the master data. The data might be personal information such as first name, last name, address, etc. Do you want to change your data within each institution separately? Or would you prefer to follow the only-once principle? Naturally, you would like to submit it once to one institution and propagate data atomically in other institutions. The later statement follows the EU [Once Only Principle](https://ec.europa.eu/digital-building-blocks/wikis/display/CEFDIGITAL/Once+Only+Principle).

For years, there has been a significant investment in integrating these kinds of systems across different countries. You remember the terms of service buses, SOA, BPEL, and others. In general, it's a good architectural pattern of integrating distributed systems. The right question might be whether it is fast to develop and cost-effective.

Still, can we do more on that topic? Can we leverage blockchain for integration and data synchronization? In the end, isn't a blockchain a distributed system suitable for data replication across multiple organizations? Yes, it is! We can design a system that will leverage distributed ledger, one of the core capabilities of blockchain, to make real-time data synchronization across multiple organizations. Hyperledger Fabric is a perfect match for it. Take a look at the diagram below. Notice the green circle uniting all three institutions, making the data synchronization for the "Person" entity enabled by the distributed ledger. That is a fast and cost-effective data synchronization that will allow you to change your data only once in a single institution, while all the others will have a real-time update.

![](images/uc-egov-2.png)

What else Hypeledger Fabric brings to the government processes? The true power of the blockchain lies in the automation of smart contracts. Imagine an example where you are becoming a fresh parent. You would probably (1) suspend your working contract and (2) activate the maternity/paternity grant to receive compensation from the government. So you are taking two actions with two different government entities. Let's assume that maternity/paternity grants are provided by the Work and Pension Department, while the working contracts for the case of income taxation reside in Tax Authority. Activating maternity/paternity grants implies suspension of your working contract since your employer will not pay you for the grant duration. So it's logical to notify Tax Authority about the suspension of the working contract to get the exclusion of income tax based on salary. Again, by default, that action requires you to talk with two institutions, submitting forms and papers to both. Could we make it more simple? Can we shape better citizen UX? Is there a cost-effective method? We can achieve this process automation by using smart contracts or, more precisely, chaincodes in Hyperledger Fabric.

The picture below describes how smart contracts can automate "Contract" and "Grant" entities. Each time a citizen receives an approved maternity/paternity leave grant, all working contracts should be automatically suspended until the leave expires. In that case, you would need to visit only one institution and let the blockchain do the magic in all other institutions. It's an excellent example of frictionless government experience relying on technical enablers capable of doing so.

![](images/uc-egov-3.png)

What is the next step? Let's build a blockchain network and independent government systems.

![](images/uc-egov-4.png)

## Build Demo
------

### Create Tax Authority (Founder Org) instance of Oracle Blockchain
The first step to demonstrate our use case is to create a founder organization - <code>Tax Authority</code>.
Locate Blockchain Platform (Developer Services -> Blockchain Platform) in the OCI menu and click on it.      

![Menu](images/general-menu-1.png)

Press <code>Create Blockchain Platform</code> button.

![Create Founder](images/founder-create-1.png)

The Dialog will open to specify parameters for the founder organization. Make sure you select <code>Create a new network</code> since we create the founder instance. Founder instance has the privilege to control joiners into the network. Select <code>Hyperledger Fabric v2.2.4</code>, or later if available. Since we are building a prototype, we will use <code>Standard Edition</code>, bringing 2 OCPUs (two physical cores), 50GB of storage, and 2 peer nodes.
Additionally, it will create 3 orderer nodes and one CA node. Peer nodes are responsible for the data store of blockchain transactions and a world state. Orderer nodes seal transactions in blocks and act as consensus enablers. CA node issues certificates for network members. You would like to have more peer nodes in the production environment due to security and availability requirements.

![Create Founder](images/founder-create-2.png)

Click on the button <code>Create</code>. Your instance is getting provisioned in status <code>Creating</code>.

![Create Founder](images/founder-create-3.png)

After a couple of minutes, the founder instance will be ready to play.

![Create Founder](images/founder-create-4.png)

We leave the founder instance alone for a couple of minutes while we provision the member instance in the following chapter.

### Create Work and Pension Department (Member Org) instance of Oracle Blockchain
The second step is to create a member organization to join the network created in the previous step - <code>Work and Pension Department</code>.
Locate Blockchain Platform (Developer Services -> Blockchain Platform) in the OCI menu and click on it.

![Menu](images/general-menu-1.png)

Press <code>Create Blockchain Platform</code> button.

![Create Founder](images/founder-create-1.png)

The dialog will open to specify parameters for the member organization. Make sure you select <code>Join an existing network</code>. Member instance network served by the founder organization. Select <code>Hyperledger Fabric v2.2.4</code>, or later if available. We will use <code>Standard Edition</code> again. I will use 2 OCPUs (two physical cores), 50GB of storage, and 2 peer nodes, without any orderers or CAs.

![Create Founder](images/member-create-1.png)

Click on the button <code>Create</code>. Your instance is getting provisioned and soon will be available.

![Create Founder](images/member-create-2.png)

### Connect Tax Authority (Founder Org) with Work and Pension Department (Member Org)
 
Let's connect blockchain organizations created in previous chapters. Admins of the instances will collaborate to exchange essential information.

1. Login to <code>Work and Pension Department</code> (Member Org) service console
![](images/connect-export-certificates-member-1.png)
2. Go to the step 2 and click <code>Export</code> button to export certificates into a JSON file.
![](images/connect-export-certificates-member-2.png)
3. Login to <code>Tax Authority</code> (Founder Org) service console, and click on <code>Add Organizations</code>
![](images/connect-export-certificates-member-3.png)
4. Select the exported json file from the 2nd step, describing <code>Work and Pension Department</code> organization, and press <code>Add</code>.
![](images/connect-export-certificates-member-4.png)
5. <code>Work and Pension Department</code> (Member Org) is successfully added. Click on <code>Export Orderer Settings</code> from the modal window, and save the JSON file.
![](images/connect-export-certificates-member-5.png)
6. <code>Open Work and Pension Department</code> (Member Org) service console again, and select <code>Step 3</code>. Select the JSON from the previous step, and click <code>Import</code>. You have just imported <code>Tax Authority</code> (Founder Org) orderers into the  <code>Work and Pension Department </code> (Member Org) organization, making it ready to sign the blocks.
![](images/connect-export-certificates-member-6.png)
7. Click on <code>Step 4</code> to complete the process and exit the wizard.
8. exchange orderers
9. create channel

### AppBuilder Intro
Oracle Blockchain App Builder is a toolset for rapid and manageable Hyperledger Fabric development that helps to develop, test, debug, and deploy smart contracts (chaincodes). It is comprised of:
* [CLI](#install-appbuilder-cli)
* Visual Studio Code extension
* Specification files

Visual Studio Code extension is user friendly managment of CLI operations. In this tutorial, I will use only CLI.

App Builder process starts with design of Specification file, which is then transformed into the scaffold chaincode project. It's a boilerplate project implemented in preffered language: TypeScript or Go. Scaffold chaincode project will save you a lot of time, since it generates assets with basic CRUD operations. Even if you don't add any custom operations, generated project will server as a chaincode capable of executing basic chaincode operatiosn, such as creating, reading, updating and deleting assets.
![](images/appbuilder-process-1.png)
Running and deployind options from the upper diagram are closely coupled with the ochain CLI after the scaffold chaincode is generated.

### Install AppBuilder CLI
Installation of App Builder is dependent upon your operating system. Please follow the detailed guide from [official docs](https://docs.oracle.com/en/cloud/paas/blockchain-cloud/usingoci/install-and-configure-dev-tools-cli.html).

If the installation was successful, you can run the ```ochain``` command. Type ```ochain``` into the terminal and you will get a list of available commands:
* <code>init</code> - Initialize a new chaincode project
* <code>run</code> - Run chaincode project locally in debug mode
* <code>stop</code> - Shutdown all chaincode services locally
* <code>invoke</code> - Invoke a chaincode transaction locally
* <code>query</code> - Invoke a chaincode query locally
* <code>package</code> - Package and archive a chaincode project for manual deployment using OBP Admin UI
* <code>deploy</code> - Deploy chaincode project to remote OBP
* <code>sync</code> - Synchronize changes from spec file to the required chaincode
* <code>upgrade</code> - Upgrade chaincode project

### AppBulder Specification File


First step in chaincode development is design of App Builder [specification file](https://docs.oracle.com/en/database/other-databases/blockchain-enterprise/21.1/user/input-configuration-file.html). Each chaincode is built by exactly one specification file. Specification file is structured in the following way:
```yaml
assets: 
    name:
    properties:
        name:
        type:
        id:
        derived:
           strategy:
           algorithm:
           format:
        mandatory:
        default:
        validate:
    methods:
        crud:
        others:
    type:
customMethods:
```

### Develop DLT Data Synchronization



```yaml
assets:
    - name: employer
    - name: person
    - name: contract
```
```yaml
assets:
    - name: grant
    - name: pension
```
### Develop UC 2
