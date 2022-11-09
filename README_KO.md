# Welcome

HAVAH 는 [ICON](https://www.icon.foundation/) 을 기반으로 한 블록체인 엔진입니다. 스마트 컨트랙트 작성 및 배포, Transaction 요청, json-RPC 연동 등 기본적인 동작은 ICON의 동작방식과 동일합니다.

이 문서는 테스트넷 접근 정보 및 스마트 컨트랙트 작성에 관해 안내하기 위해 만들어졌습니다.
 

## 스마트 컨트랙트

HAVAH는 아이콘 자바 스코어와 동일한 방식으로 스마트 컨트랙트를 작성합니다.

먼저 아이콘 자바 스코어 샘플 문서를 확인하시길 바랍니다.

- [ICON Java SCORE sample](https://github.com/icon-project/java-score-examples)


스마트 컨트랙트 작성시 사용되는 자바 스코어 API 및 유틸리티 라이브러리(scorex) 는 아래 문서를 참고하세요.

- [Java SCORE API Document](https://www.javadoc.io/doc/foundation.icon/javaee-api/latest/index.html)

- [scorex](https://www.javadoc.io/doc/foundation.icon/javaee-api/latest/index.html)
 

스마트 컨트랙트 작성시 허용된 자바 메소드만 사용할수 있습니다. 허용 메소드 목록은 아래 링크에서 확인하실 수 있습니다.

- [Java SCORE allowed methods](https://github.com/icon-project/devportal/blob/master/java-score-1/allowed-methods)
 

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

- Fauset

	- 지갑주소를 전달하시면 해당 주소로 100HVH를 입금해드립니다.


## 개발 참고 사이트

아이콘 데브 포탈을 참고하시면 더 많은 정보를 얻으실 수 있습니다.

- [ICON DEV PORTAL](https://docs.icon.community/)

- [ICON goloop](https://github.com/icon-project/goloop)