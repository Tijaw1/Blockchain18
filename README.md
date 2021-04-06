# Blockchain18

This is a guide to how to start and run a Blockchain network, with a particular emphasis on Proof of Authority concenses algorithm.

Make sure the following softwares are properly installed and running:
- Git-bash
- MyCrypto: an open-source, client-side interface that allows users to interact and manage their Blockchain wallets.
- Go Ethereum (geth): an open source tool to create the blockchains from scratch.
- Puppeth: Puppeth is a CLI wizard that aids in creating a new Ethereum network down to the genesis, bootnodes, signers, ethstats, faucet, dashboard and more, without the hassle that it would normally take to configure all these services one by one (source: Ethereum blog)

Procedure for POA transaction:
- Create a directory for the Blockchain
     - mkdir Blockchain
- Create nodes within the Blockchain directory using the geth command:
     - geth.exe account new --datadir node1
- When prompted, create a password for the particular node
- Save the password created and the account address using the command:
     - echo 'the password you created here' > node1/password.txt
     - echo 'node1 public address here' >> accounts.txt
- repeat the node1 instructions for node 2
![1](https://user-images.githubusercontent.com/74274975/113787474-efd50f80-96ef-11eb-8e2b-8c36a9bc12f2.PNG)
- Run puppeth using the following command in the Blockchain-Tools directory:
     - ./puppeth
- Assign the network a name and press enter
     - puppernet (an example)
- Select 2, to start configuring a new genesis block and press enter
- Select 1, to create new genesis from scratch and press enter
- Select 1 to choose Proof of Work consensus engine or Select 2 to choose Proof of Authority consensus engine. In this case, Select 2 to choose Proof of Authority and press enter.
- For the how many seconds shouls the block take, you can choose your number ... the default is 15sec
- Addresses: use Mycrypto Wallet addresses and/or the node addresses (as many as chosen)
- For thr precompile prompt:
     - Type No 
- Assign the chain ID value and save the value for future use
- select 'Manage Existing Genesis' in the next prompt and hit enter
- Select 2 on the next prompt for 'Export Genesis Configurations' option and press enter
- Exit puppeth using Ctrl+C keys
- The above puppeth configuration is shown in the example picture below:
  ![puppeth_config1](https://user-images.githubusercontent.com/74274975/113791808-4c88f800-96f9-11eb-81a7-1b972eccecbb.PNG)
  ![puppeth_config2](https://user-images.githubusercontent.com/74274975/113791818-514dac00-96f9-11eb-8998-ccef7bfcb400.PNG)

Working on the Blockchain:
- Initialize the nodes using the following geth command
     - geth.exe init networkname.json --datadir node1
     - geth.exe init networkname.json --datadir node2
     - Make sure it shows success as indicated in the example picture below
     ![node5 initialization](https://user-images.githubusercontent.com/74274975/113791612-e8feca80-96f8-11eb-9783-4eaffbf70bac.PNG)
     
- Launch the node to mining using the command:
     - geth.exe --datadir node1 --mine --miner.threads 1 --unlock "node1-address" --password node1/password.txt  --rpc --allow-insecure-unlock
     - Copy and save the enode:// values from node1. It is found on 'Started P2P Networking' line 
- Launch second node using the command:
     - geth.exe --datadir node2 --unlock "node2-address" --mine --port 30304 --bootnodes <node1 enode:// value> --password node2/password.txt  --allow-insecure-unlock

Running MyCrypto:
- Open the MyCrypto App
- Select 'Add Custom Node' and add the custon network information in genesis
- Make sure to select 'Custom' on the Network dropdown selection
- Select the currency and enter the Chain ID you selected in Genesis
- For URL, enter http://127.0.0.1:8545 and click on Sane and use Custom node
     - check that the system is connected to the Custom network
![MyCrypto1](https://user-images.githubusercontent.com/74274975/113790705-cbc8fc80-96f6-11eb-9da3-950b0174ce56.PNG)

- Import the keys from keystore file of node1, node1/keystore directory. This will import the private key
![MyCrypto2](https://user-images.githubusercontent.com/74274975/113790917-53af0680-96f7-11eb-9323-2819aed5deb8.PNG)

- Send a transaction from node1 to node2 accounts
![Transaction](https://user-images.githubusercontent.com/74274975/113791046-996bcf00-96f7-11eb-85c6-83ec98f0db06.PNG)
![Transaction_1](https://user-images.githubusercontent.com/74274975/113791081-b4d6da00-96f7-11eb-9724-38cf0f999772.PNG)

- Copy the transaction hash and use it in the Tx status or click on the Tx Status on the transaction popup 
![Transaction_2](https://user-images.githubusercontent.com/74274975/113791409-68d86500-96f8-11eb-8c35-4a5a9af40315.PNG)

- The transactio should show successful to indicate a successful transfer action.
![Transaction_Final](https://user-images.githubusercontent.com/74274975/113791280-26af2380-96f8-11eb-85c7-b56a7d1623e2.PNG)
