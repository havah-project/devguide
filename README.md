# HAVAH developer's guide

HAVAH is a blockchain engine based on [ICON](https://www.icon.foundation/). Basic operations such as smart contract creation and distribution, transaction request, and json-RPC interworking are the same as those of ICON.

This document contains the guide for testnet access information and smart contract creation.
 

## Smart contract

HAVAH writes smart contracts in the same way as ICON Java SCORE.

Please check the HAVAH Smart Contract sample document first.

- [HAVAH Smart Contract sample](https://github.com/havah-project/smart-contract-examples)


Refer to the document below for the Smart Contract API and utility library (scorex) used when writing smart contracts.

- [Smart Contract API Document](https://www.javadoc.io/doc/foundation.icon/javaee-api/latest/index.html)

- [scorex](https://github.com/icon-project/javaee-scorex)
 
build.gradle
```groovy
dependencies {
    implementation 'foundation.icon:javaee-scorex:0.5.3'
}

optimizedJar {
    from {
        configurations.runtimeClasspath.collect { it.isDirectory() ? it : zipTree(it) }
    }
}
```


Only allowed Java methods can be used when writing smart contracts. A list of allow methods can be found at the link below.

- [Smart Contract allowed methods](https://github.com/icon-project/devportal/blob/master/java-score-1/allowed-methods)
 

## HAVAH SDK

Currently, there is no dedicated SDK for HAVAH. Integration is possible using the ICON SDK.

- [Java SDK](https://docs.icon.community/icon-stack/client-apis/java-sdk)


## Vega (testnet)

Vega is the name of the HAVAH testnet. Access information is as follows.

- JSON-RPC API endpoint

	- [https://ctz.vega.havah.io/api/v3](https://ctz.vega.havah.io/api/v3)

- nid (network id)

	- 0x101

- Block Explorer (HAVAH scan)

	- [https://scan.vega.havah.io](https://scan.vega.havah.io)

- Faucet

	- If you pass your wallet address, we will deposit 100HVH to that address.

## Mainnet

The access information of HAVAH mainnet is as follows.

- JSON-RPC API endpoint

	- [https://ctz.havah.io/api/v3](https://ctz.vega.havah.io/api/v3)

- nid (network id)

	- 0x100

- Block Explorer (HAVAH scan)

	- [https://scan.havah.io](https://scan.havah.io)

## HAVAH CHAIN NODE

HAVAH blockchain nodes can be operated using Docker images.

- HAVAH chain node docker

	- [https://github.com/havah-project/havah-chain-node-docker](https://github.com/havah-project/havah-chain-node-docker)

### Keystore

A keystore file can be created using the goloop CLI. See link below.

- [https://github.com/havah-project/goloop-havah/blob/main/doc/goloop_cli.md#goloop-ks-gen](https://github.com/havah-project/goloop-havah/blob/main/doc/goloop_cli.md#goloop-ks-gen)

Or refer to Tips, 'How to create a keystore file with a private key'.

### Node types

Due to the delegated nature of the ICON network, there are currently two different types of nodes: API Endpoints and Validators. API Endpoints are also called Citizen nodes.

#### API Endpoints (=Citizen)

- Stores full blockchain state
- Read capabilities
- Provides data to users

#### Validators

- Stores full blockchain state
- Read / write capabilities
- Provides data to API Endpoints and other validators

 For more information on node types, please refer to the link below.
 
 - [API Endpoints](https://docs.icon.community/concepts/network/api-endpoints)
 - [Validator nodes](https://docs.icon.community/concepts/network/validator-nodes)

## Tips

- Building in a windows WSL + ubuntu environment, the run directory must be located in the Ubuntu filesystem, not below /mnt/c

- If the javaee/exec/build/native/ folder is empty after make in the project folder, you need to create a native file by proceeding make in javaee/

- How to create a keystore file with a private key:

	1. Install ICONex chrome web browser extenstion.

		- [ICONex - chrome web store](https://chrome.google.com/webstore/detail/iconex/flpiciilemghbmfalicajoolhkkenfel)

	2. Select ICONex - 'Access My Wallet' - 'Add Wallets'
	
	3. Select 'Load Wallet' in the Add Wallet dialog.
	<img src="./img/iconex_en_1.png" width="50%" />
	
	4. Select 'Enter private key' in the Load Wallet dialog.
	<img src="./img/iconex_en_2.png" width="50%" />
	
	5. Select 'ICON (ICX)' and enter the private key.
	<img src="./img/iconex_en_3.png" width="50%" />
	
	6. Select the 'Backup wallet' menu of the wallet.
	<img src="./img/iconex_en_4.png" width="50%" />
	
	7. Enter Wallet password.
	
	8. You can download the keystore file by selecting 'Download Keystore file(wallet backup file)'.
	<img src="./img/iconex_en_5.png" width="50%" />

- When sending a transaction using the goloop CLI tool, you need to add the --estimate option to get an estimated step.

```shell
goloop rpc sendtx transfer \
    --uri http://localhost:9080/api/v3 \
    --key_store ./data/keystore_gov.json --key_password gochain \
    --nid 0x110 --step_limit 1000000 \
    --to hxb6b5791be0b5ef67063b3c10b840fb81514db2fd \
    --estimate \
    --value 20000000000000000000
```

- Transation fee is calculated as step price * number of steps. To get the estimated fee, multiply the stepprice by the estimated step found with the --estimate option. The step price can be obtained by calling getStepPrice of Chain Score (cx0000000000000000000000000000000000000000).

```shell
goloop rpc call --to cx0000000000000000000000000000000000000000 \
    --uri http://localhost:9080/api/v3 \
    --method getStepPrice
```

## Development reference site

Please refer to the ICON DEV PORTAL for more information.

- [ICON DEV PORTAL](https://docs.icon.community/)

- [ICON goloop](https://github.com/icon-project/goloop)
