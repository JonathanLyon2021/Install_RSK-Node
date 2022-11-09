# Install_RSK-Node
This is Exercise 20 from MI4 in Kingsland Universities Blockchain Developer Program.

# Overview

RSK is the Smart Contract platform of Bitcoin. Its engine is a forked version of the EVM (Ethereum Virtual Machine),
and the RVM (RSK Virtual Machine) is compatible with Ethereum Smart Contracts and the tools used to deploy and
interact with them.

The Smart Bitcoin (R-BTC) is the native token in RSK and it is used to pay for the gas required for the execution of
transactions. It is pegged 1:1 with Bitcoin, which means in RSK there are exactly 21M R-BTC. A 2-way peg (2WP)
allows the transfer of bitcoins from the Bitcoin blockchain to the RSK blockchain and vice-versa.

# Goals

• Run a local RSK blockchain node.
• Deploy and interact with the contracts deployed on the RSK blockchain.

# Prerequisites

• Java JDK 14 *https://www.oracle.com/java/technologies/javase-jdk14-downloads.html*
• Node v13.5.0 *https://nodejs.org/download/release/v13.5.0/*
• NPM v6.13.4 Already bundled with Node.
• Truffle v5.1.19 npm install -g truffle@5.1.19
• Solc v0.6.0 npm install -g solc@0.6.0
• RSKJ-Core v1.3.0 *https://github.com/rsksmart/rskj/releases/tag/WASABI-1.3.0*

# 1. Download and Run RSK

1. Download rskj-core-1.3.0-WASABI-all.jar on *https://github.com/rsksmart/rskj/releases/tag/WASABI-1.3.0*
Place it on your preferred directory. Starting now, this directory will be referred to as your workspace.

2. Add the configuration file node.conf for RSKJ. Open up your favorite editor in the workspace and copy the
contents of the following gist:
*https://gist.github.com/24thsaint/85cb2d3f8c3cd7b42cf6b3d13b48ce97*

3. Open up a terminal on your workspace and run an RSK node. Note that you will not see any print statements
on the console and it looks like the command is not responding. That is normal.

    java -Drsk.conf.file=node.conf -cp rskj-core-1.3.0-WASABI-all.jar co.rsk.Start
    
# 2. Install and Configure Truffle Project

1. If you don’t have truffle and solc already, run the following command:

        npm install -g truffle@5.1.19
        npm install -g solc@0.6.0

You may need administrative permissions to continue with the installation.
2. On a new terminal, initialize a truffle project and accept any prompts that may show up:

    truffle init
    
3. Configure truffle-config.js, replace it with the following content:
*module.exports = {
networks: {
development: {
host: "127.0.0.1",
port: 4444,
network_id: "*",
},
},
compilers: {
solc: {
version: "0.6.0",
},
},
};*
4. Verify if you are successfully connected to RSKJ. 

        truffle console
        web3.eth.getAccounts()

5. Select the default account where transactions such as contract deployment will occur by default. In this
exercise, choose the first account, then add it to truffle-config.js
    
# 3. Implement and Deploy a Smart Contract

1. To jumpstart things, let’s use Truffle to create a contract template file for us on the correct directory:

        truffle create contract SimpleStorage

This creates a SimpleStorage.sol contract template file on the contracts/ folder.

2. Use your favorite editor to implement the SimpleStorage contract. Remember to use solidity ^0.6.0:

3. Setup Migrations. Create a 2_deploy_contracts.js in the migrations folder with this content:

4. With the files in place, you are now ready to deploy the smart contract. In your terminal, issue the following
commands:

        truffle compile
        truffle migrate

It will take some time because the block where the transaction is included must be mined.
    
Awesome! You have successfully deployed a contract in the local RSK blockchain.
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
