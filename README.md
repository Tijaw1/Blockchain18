![1](https://user-images.githubusercontent.com/74274975/113787450-e77cd480-96ef-11eb-9eb5-5320fcabef54.PNG)
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
![1](https://user-images.githubusercontent.com/74274975/113787474-efd50f80-96ef-11eb-8e2b-8c36a9bc12f2.PNG)
- Run puppeth using the following command in the Blockchain-Tools directory:
     - ./puppeth
