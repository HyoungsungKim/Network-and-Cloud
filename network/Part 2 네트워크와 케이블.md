# Part 2 네트워크와 케이블

## 이더넷

이더넷 : Carrier Sense Multiple Access/Collisionm Detection (CSMA/CD) 방식

- 통신하고자 하는 컴퓨터가 통신을 하고 있지 않으면 무조건 자기 데이터를 실어서 보낸 후 잘 갓늦지 확인 함.
- 만약 동시에 2개의 컴퓨터가 동시에 보낼 경우 충돌 (Collision) 발생
  - 이럴경우 랜덤한 시간 동안 대기 후 다시 전송

## 토큰링 (TokenRing)

네트워크에서 오직 한 PC, 즉 토큰을 가진 PC만이 네트워크에 데이터를 실어 보낼 수 있음.

- 데이터를 다 보내고 나면 바로 옆 PC에 토큰을 건네줌
- 만약 전송 할 데이터가 없다면 옆 PC에게 토큰을 건네줌

## UTP 케이블

- TP cable : Twisted-pair cable
  - Unshieled TP(UTP)
  - Shieled TP(STP)
- 카테고리 1 : 전화망 -> 데이터 전송에는 좋지 않음
- 카테고리 2 : 4Mbps
- 카테고리 3 : 10 Base T 네트워크에 사용되는 케이블.
- 카테고리 4 : 토큰링 네트워크에서 사용 됨
- 카테고리 5, 6, 7 : 카테고리 숫자 올라갈 수록 대역폭 넓어짐

## 케이블

10 Base T : 앞에 나오는 숫자는 속도를 나타냄.

- 여기서 10이란 10 Mbps의 속도를 지원하는 케이블
- Base란 이 케이블이 Baseband영 케이블이라는 것을 알려 줌
  - Baseband : 디지털 방식
  - Broadband : 아날로그 방식
  - T : TP케이블이라는 것을 의미
  - 만약 10 Base 5 처럼 뒤에 숫자가 온다면 최대 통신 거리 의미(5는 500 미터)
    - 10Mbps의 속도로 500미터까지 통신 가능
- 전송 속도가 빨라질수록 전송 거리는 점점 짧아짐

## 맥 어드레스 (MAC address)

MAC : Media Access Control

- 네트워크상에서 서로를 구분할 일종의 주소
  - IP주소와 차이점?
  - IP주소로 통신 할 때에도 맥 어드레스를 사용 함
  - IP주소를 맥 어드레스로 바꾸는 절차가 존재 함(ARP:Address Resolution Protocol)
  - Phical address라고 불리는 것이 맥 어드레스임
  - 호스트 사이에 라우터가 존재 할 경우 라우터의 맥 어드레스에 통신하고자 하는 호스트의 맥 어드레스 요청 함
    - 라우터의 맥 어드레스는 알고 있음

## 유니캐스트, 브로드캐스트, 멀티캐스트

네트워크에서 통신하는 방식에 따른 구분

- 1대 1로 하는 통신 방식 : 유니캐스트
- 어떤 그룹을 대상으로 하는 통신 방식 : 브로드캐스트
- 전부를 대상으로 하는 통신 방식 : 멀티캐스트

### 유니캐스트

출발지의 목적지의 맥 주소를 사용 함.

- 받는 PC의 주소를 프레임 안에 써넣는데, 이때 받는 PC가 하나여야 함.
  - 수신 했을 때 자신의 랜카드 맥주소와 프레임에 있는 맥주소가 다르다면 프레임을 버림
  - PC의 CPU까지 영향을 주지 않기 때문에 브로드캐스트보다 빠름
- 현재 네트워크상에서 가장 많이 사용되는 통신방식임

### 브로드캐스트

로컬랜에 붙어 있는 모든 네트워크 장비들에게 보내는 통신

- 로컬 랜이란 라우터에의해서 구분된 공간 -> 브로드캐스트 도메인이라고도 불림.
- 네트워크 안의 모든 네트워크 장비들에 통신 할 때 쓰기 위한 방식.
- FFFF:FFFF:FFFF:FFFF를 맥주소로 사용
- 프레임을 버리지 않고 CPU에 전달 함
- 상대편의 맥주소를 모를 때 사용 함 (ARP : Address Resolution Protocol)
  - IP주소만 알 때 맥 주소를 알기 위해 사용 함

### 멀티캐스트

같은 정보를 동시에 여러명에게 보내야 할 때(e.g., 200명 중 150명)

- 브로드캐스트를 사용 할 경우 정보를 받을 필요 없는 사람들 까지 받게 됨
  - 브로드캐스트로 인한 성능 저하 발생
- 멀티캐스트는 보내고자 하는 그룹 멤버들에게만 보냄
- 라우터나 스위치에서 이 기능을 지원 해주어야만 쓸 수 있음

## OSI 7 Layer

- Application layer
  - 전송 단위 : 데이터
- Presentation layer
  - 전송 단위 : 데이터
- Session layer
  - 전송 단위 : 데이터
- Transport layer :
  - 컨트롤과 에러 복구(e.g., TCP, UDP)
  - 전송 단위 : 세그먼트
- Network layer : 라우터
  - 데이터를 목적지까지 안전하고 빠르게 전송
  - 전송 단위 : 패킷
- Data link layer : 스위치, 브리지
  - 통신에서 오류 찾고 재전송하는 기능
  - 맥 어드레스로 통신
  - 전송 단위 : 프레임
- Physical layer : 데이터 케이블, 허브
  - 데이터 오류 확인하지 않고 0과 1로 전송
  - 전송 단위 : 비트

## 프로토콜

인터넷을 사용하기 위해서는 모든 PC가 TCP/IP라는 프로토콜을 사용해야 함.