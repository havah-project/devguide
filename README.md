# Welcome

HAVAH 는 ICON 을 기반으로 한 블록체인 엔진입니다. 스마트 컨트랙트 작성 및 배포, Transaction 요청, json-RPC 연동 등 기본적인 동작은 ICON의 동작방식과 동일합니다.

이 문서는 테스트넷 접근 정보 및 스마트 컨트랙트 작성에 관해 안내하기 위해 만들어졌습니다.
 

## 스마트 컨트랙트

HAVAH의 스마트 컨트랙트를 작성하는 방법은 아이콘 자바스코어를 작성하는 방식과 동일합니다.

먼저 아이콘 자바스코어 샘플 문서를 확인하시길 바랍니다.

- [아이콘 자바스코어 샘플 git](https://github.com/icon-project/java-score-examples)


스마트 컨트랙트 작성시 사용되는 JAVA 스코어 API 및 유틸리티 라이브러리(scorex) 는 아래 문서를 참고하세요.

- [자바스코어 API Document](https://www.javadoc.io/doc/foundation.icon/javaee-api/latest/index.html)

- [scorex](https://www.javadoc.io/doc/foundation.icon/javaee-api/latest/index.html)
 

스마트 컨트랙트 작성시 미리 지정된 JAVA method만 사용할수 있습니다. 사용 가능 method 목록은 아래 링크에서 확인하실 수 있습니다.

- [자바스코어 allow methods](https://github.com/icon-project/devportal/blob/master/java-score-1/allowed-methods)
 

## Havah SDK

현재 HAVAH 전용 SDK는 준비되어 있지 않습니다. ICON SDK를 사용하여 연동이 가능합니다.

- [JAVA SDK](https://docs.icon.community/icon-stack/client-apis/java-sdk)


## Vega (testnet)

Vega 는 HAVAH 테스트넷의 이름입니다. 접근 정보는 아래와 같습니다.

- JSON-RPC API endpoint

	- https://ctz.vega.havah.io/api/v3

- nid (network id)

	- 0x101

- Block Explorer (HAVAH scan)

	- https://scan.vega.havah.io

- Fauset

	- 지갑주소를 전달하시면 해당 주소로 100HVH를 입금해드립니다.


## 개발 참고 사이트

아이콘 데브 포탈을 참고하시면 더 많은 정보를 얻으실 수 있습니다.

- [아이콘 데브 포탈](https://docs.icon.community/)

- [아이콘 goloop git](https://github.com/icon-project/goloop)