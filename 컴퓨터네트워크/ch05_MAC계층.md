# ch05 MAC


## LLC 계층
- MAC 계층에서 공통적인 부분 모음
- MAC 보다 위

## MAC 계층
> Multiple Access Channel(다중 접근 채널)

- 다중 연결을 활용하여 공유매체에게 프레임을 전송
- 동시에 전송이 이뤄지면 **충돌**가능성 존재
- 해결방법
    - 충돌 후속 조치
        - 이더넷
            - CSMA/CD (Carrier Sense Multiple Access, Collision Detection)
            - 충돌을 감지 하면 중단 후 재전송
            - 다만 매체가 길어지면 프레임 전송 지연이 증가하여, 충돌 발생 가능성이 증가함

    - 충돌 방지
        1. 타임 슬롯(time slot) 배정
        2. 토큰 활용
            - 토큰 버스
                - 물리적 버스 구조
                - 논리적 링 구조
            - 토큰 링
                - 물리적/논리적 링구조
                - 대기 모드/전송모드로 동작

## 이더넷
- 1-persistent CSMA
    - 유효상태 여부 계속 watch
    - 상태가 가능해지면 바로 연결 시도
- Non-persistent CSMA
    - 유효상태 여부 임의 시간 동안 wait 후 watch
- P-persistent CSMA
    - Non + p확률
    - 슬롯 채널
    - 채널이 사용 중이면 다음 슬롯까지 대기후 다시 채널 감지를시작
    - 가능해지면 p의 확률로 프레임 전송

## 허브와 스위치
- 트랜시버/리피터
- 허브(hub, dummy hub)
    - 외형상 스타형 구조로 허브에 연결
    - 내부적으로는 공유 버스 방식
- 스위칭 허브(switching hub)
    - 스위칭 기능
        - 모든 호스트에게 프레임 전송을 하지 않는다( 목적지 호스트에게만 전송)
        - 따라서 동시에 여러 호스트가 데이터 전송 가능
    - 장점
        - 스위치 허브의 용량이 허용되면, 각각의 호스트는 할당된 LAN 용량을 모두 사용 가능
        - dummy hub에서 스위치 허브로의 전환이 간단함(hub만 교체)

## 프레임
- MAC 프레임 = MAC 헤더 + LLC 프레임 + MAC 트레일러

- 이더넷 프레임구조
    - MAC 헤더
        - Preamble
            - 수신 호스트와 송신 호스트의 클록 동기 sync
        - Start Delimiter
            - 프레임의 시작 위치 구분
        - Destination Address ( 수신호스트 MAC 주소 )
        - Source Address ( 송신호스트 MAC 주소 )
        - Length
            - Data 필드(LLC프레임)에 포함된 가변 길이의 전송 데이터 크기
    - LLC 프레임 ( = Data Field )
    - LLC 트레일러(꼬리)
        - Pad
            - padding 시켜주는 용량 맞춰주는 용도
            - CheckSum

## 토큰 버스의 프레임 구조

## 토큰 링의 프레임 구조



