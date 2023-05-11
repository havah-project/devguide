# HAVAH developer's guide

HAVAH 는 [ICON](https://www.icon.foundation/) 을 기반으로 한 블록체인 엔진입니다. 스마트 컨트랙트 작성 및 배포, Transaction 요청, json-RPC 연동 등 기본적인 동작은 ICON의 동작방식과 동일합니다.

이 문서는 테스트넷 접근 정보 및 스마트 컨트랙트 작성에 관해 안내하기 위해 만들어졌습니다.
 

## 스마트 컨트랙트

HAVAH는 아이콘 자바 스코어와 동일한 방식으로 스마트 컨트랙트를 작성합니다.

먼저 하바 스마트 컨트랙트 샘플 문서를 확인하시길 바랍니다.

- [HAVAH Smart Contract sample](https://github.com/havah-project/smart-contract-examples)


스마트 컨트랙트 작성시 사용되는 API 및 유틸리티 라이브러리(scorex) 는 아래 문서를 참고하세요.

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

스마트 컨트랙트 작성시 허용된 자바 메소드만 사용할수 있습니다. 허용 메소드 목록은 아래 링크에서 확인하실 수 있습니다.

- [Smart Contract allowed methods](https://github.com/icon-project/devportal/blob/master/java-score-1/allowed-methods)

### ICON JAVA SCORE Toutorials

ICON 자바 스코어 튜토리얼을 참고하실수 있습니다.

- Java Tutorial Part 1: Setting Development Environment and Writing Smart Contract
https://coinmarketcap.com/community/articles/644b8d1cfec63d16dc58e86e/

- Java Tutorial Part 2: Deploying the Smart Contract and Interacting with the Smart Contract Onchain
https://coinmarketcap.com/community/articles/6453908ac1d7e422b683e990/

- Java Tutorial Part 3: Unit Testing
https://coinmarketcap.com/community/articles/6458bc59058ca27821194dd5/
 

## HAVAH SDK

현재 HAVAH 전용 SDK는 준비되어 있지 않습니다. ICON SDK를 사용하여 연동이 가능합니다.

- [Java SDK](https://docs.icon.community/icon-stack/client-apis/java-sdk)


## Vega (testnet)

Vega 는 HAVAH 테스트넷의 이름입니다. 접근 정보는 아래와 같습니다.

- JSON-RPC API endpoint

	- [https://ctz.vega.havah.io/api/v3](https://ctz.vega.havah.io/api/v3)

- nid (network id)

	- 0x101

- Block Explorer (HAVAH scan)

	- [https://scan.vega.havah.io](https://scan.vega.havah.io)

- Faucet

	- 지갑주소를 전달하시면 해당 주소로 100HVH를 입금해드립니다.

## Mainnet

HAVAH 메인넷의 접근 정보는 아래와 같습니다.

- JSON-RPC API endpoint

	- [https://ctz.havah.io/api/v3](https://ctz.vega.havah.io/api/v3)

- nid (network id)

	- 0x100

- Block Explorer (HAVAH scan)

	- [https://scan.havah.io](https://scan.havah.io)

## HAVAH CHAIN NODE

Docker 이미지를 이용하여 HAVAH 블록체인 노드를 운영할 수 있습니다.

- HAVAH chain node docker

	- [https://github.com/havah-project/havah-chain-node-docker](https://github.com/havah-project/havah-chain-node-docker)

### Keystore

키스토어 파일은 goloop CLI를 사용해 생성할 수 있습니다. 아래 링크를 참고하세요.

- [https://github.com/havah-project/goloop-havah/blob/main/doc/goloop_cli.md#goloop-ks-gen](https://github.com/havah-project/goloop-havah/blob/main/doc/goloop_cli.md#goloop-ks-gen)

혹은 Tips의 '하바지갑에서 생성한 개인 키로 키스토어를 생성하는 방법'을 참고하십시오.

### Node types

HAVAH 블록체인 네크워크에는 두 가지 유형의 노드가 있습니다. API Endpoints와 Validator 노드입니다. API Endpoints는 Citizen 노드라고도 불립니다.

#### API Endpoints (=Citizen)

- 전체 블록체인 상태 저장
- 블록체인 상태 읽기 기능
- 사용자에게 데이터 제공

#### Validators

- 전체 블록체인 상태 저장
- 블록체인 상태 읽기/쓰기 기능
- API Endpoints 및 다른 Validator에 데이터 제공

 노드 타입에 대해 좀 더 자세한 정보가 필요하시면 아래 링크를 참고하세요.
 
 - [API Endpoints](https://docs.icon.community/concepts/network/api-endpoints)
 - [Validator nodes](https://docs.icon.community/concepts/network/validator-nodes)

## Tips

- windows WSL + unbuntu 환경에서 빌드시 run 디렉토리는 /mnt/c 이하가 아닌 우분투 파일시스템에 위치해야 합니다.

- 프로젝트 폴더에서 make 빌드 후에 javaee/exec/build/native/  폴더가 비어 있을 경우, javaee/ 에서 make 빌드 진행하여 native 파일을 생성해야 합니다.

- 개인 키로 키스토어 파일을 생성하는 방법:

	1. ICONex 크롬 웹브라우저 확장 프로그램을 설치합니다.

		- [ICONex - chrome 웹 스토어](https://chrome.google.com/webstore/detail/iconex/flpiciilemghbmfalicajoolhkkenfel)

	2. ICONex - '내 지갑 가기' - '지갑 추가' 메뉴를 선택합니다.
	
	3. 지갑 추가 다이얼로그에서 '지갑 가져오기'를 선택합니다.
	<img src="./img/iconex_ko_1.png" width="50%" />
	
	4. 지갑을 가져올 방법에서 '개인 키'를 선택합니다.
	<img src="./img/iconex_ko_2.png" width="50%" />
	
	5. 코인 선택은 'ICON (ICX)'을 선택하고 '개인 키 입력' 항목에 추가할 개인키를 입력합니다.
	<img src="./img/iconex_ko_3.png" width="50%" />
	
	6. 비밀키로 추가된 지갑의 '지갑 백업' 메뉴를 선택합니다.
	<img src="./img/iconex_ko_4.png" width="50%" />
	
	7. 지갑 비밀번호를 입력합니다.
	
	8. 지갑 백업 다이얼로그에서 '지갑 백업 파일(Keystore 파일) 다운로드'를 선택하면 키스토어 파일을 다운로드 받을 수 있습니다.
	<img src="./img/iconex_ko_5.png" width="50%" />

- goloop CLI 툴을 사용하여 트랜젝션 전송시 예상 스텝을 확인하려면 --estimate 옵션을 붙여야 합니다.

```shell
goloop rpc sendtx transfer \
    --uri http://localhost:9080/api/v3 \
    --key_store ./data/keystore_gov.json --key_password gochain \
    --nid 0x110 --step_limit 1000000 \
    --to hxb6b5791be0b5ef67063b3c10b840fb81514db2fd \
    --estimate \
    --value 20000000000000000000
```

- 트랜젝션 수수료는 스텝 프라이스 * 스텝수로 계산됩니다. 예상 수수료를 구하려면 --estimate 옵션으로 알아낸 예상 스텝에 스텝프라이스를 곱하여 알 수 있습니다. 스텝 프라이스는 Chain Score(cx0000000000000000000000000000000000000000)의 getStepPrice 를 호출하여 알 수 있습니다.

```shell
goloop rpc call --to cx0000000000000000000000000000000000000000 \
    --uri http://localhost:9080/api/v3 \
    --method getStepPrice
```


## 개발 참고 사이트

아이콘 데브 포탈을 참고하시면 더 많은 정보를 얻으실 수 있습니다.

- [ICON DEV PORTAL](https://docs.icon.community/)

- [ICON goloop](https://github.com/icon-project/goloop)
