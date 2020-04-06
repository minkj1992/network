# [CH09] TCP 프로토콜 구조와 플래그
> 연결지향형 TCP 프로토콜

## TCP 프로토콜
- TCP가 하는 일
	- 인터넷에 연결된 컴퓨터에서 실행되는 프로그램 간에 통신을**안정적으로 순서대로 에러없이 교환가능** 
- TCP 프로토콜의 구조 ( 20 + a(0~40) = `20 ~60`Bytes
	- `Source Port`
	- `Destination Port`
	- `Sequence Number`
	- `Acknowledgment Number`
	- `Offset`
	- `Reserved`	예약된 필드
	- `TCP Flags`
		- 아래에서 살펴본다
	- `Window` 수용가능한 데이터 용량이 얼마나 남았는지 알려주는 공간 (남아있는 TCP Buffer 공간 알려줌)
	- `Checksum`
	- `Urgent Pointer`
		- 아래에서 살펴본다
	- `TCP Options` (0~40)
## TCP 플래그
> 안정적으로 데이터 교환을 이루기 위하여 TCP는 여러가지 형태로 데이터를 보내는데, 이때 사용하는 Flag를 의미한다. (TCP 기능별 데이터 구분 Flag) 
- TCP 플래그의 종류
	- `U A P R S F` 형태로
	- Urgent: 우선순위 높음 (`Urgent Pointer`와 세트)
	- **Ack Flag**: 승인, 확인
	- Push: 밀어넣기
		- TCP는 기본적으로 버퍼에 어느정도 쌓여야 전달을 해주는데
		- 이와 상관없이 데이터를 보내버린다.
	- Reset
		- 데이터 전달과정에서 문제가 발생했고, 이에 대해서 Reset 하자는 요청
	- **Sink**(중요)
		- 연결을 시작할때 무조건 사용하는 플래그
		- S flag가 보내지고 난 다음부터, 데이터들이 동기화 된다. ( 서로 동기화 시키기 위해 확인작업 실행 )
		- 이후에 서로 상태를 주고 받으며 Sink를 한다.
	- Fin
		- 연결 종료

## TCP를 이용한 통신과정
### 1. 연결 수립 과정
- TCP를 이용한 데이터 통신을 할 때 프로세스와 프로세스를 연결하기 위해 **가장 먼저 수행되는 과정**
- `클라이언트`가 서버에게 `요청 패킷`을 보내고
- 서버가 요청 허용 패킷을 보내고
- 클라이언트는 최종적으로 수락하는 패킷을 보낸다.

위의 3개 과정을 `3Way Handshake`라고 부른다.
### 2. 3 Way Hand Shake
> Sync, Ack 숫자는 임의로 지정한다.
1. 클라이언트 -> 서버
	- Flag: `SYN`
	- `SEQ number`: 100
	- `ACK number`: 0
2. 서버 -> 클라이언트
	- Flag: `SYN` + `ACK`
	- `SEQ number`: 2000
	- `ACK number`: 101
3. 클라이언트 -> 서버
	- Flag: `ACK`
	- `SEQ number`: 101 (서버와 동기화 과정이 거쳐져서 서버 ACK 번호 사용)
	- `ACK number`: 2001
	- 동기화 적용 (3번째 요청) ACK, SYN 계산법
		- **보내는 쪽의 SEQ = 서버의 ACK**
		- **보내는 쪽의 ACK = 서버 SEQ + 1(뒤에 payload가 없기 때문에 1로 지정)**

이후 클라이언트 -> 서버로 데이터를 요청한다. (아래에 이어서 설명)

### 3. 데이터 송/수신 과정
- 규칙
	1. 보낸 쪽에서 다시 보낼 때는 `SEQ`, `ACK` 그대로
	2. 받는 쪽 `SEQ` = 받은 `ACK`
	3. 받는 쪽 `ACK` = 받은 `SEQ` + 받은 페이로드(데이터) 크기

- 예시( 데이터 보내기 )
1. 클라이언트 -> 서버 (3way handshake 이후 데이터를 보내는 상황)
	- Flag: `PSH` + `ACK`
		- 데이터를 push, ack를 통해 잘 받았냐 요청
	- `SEQ number`: 101
	- `ACK number`: 2001
		- 3way 마지막 과정과 같으 seq, ack 값
2. 서버 -> 클라이언트
	- Flag: `SYN` + `ACK`
	- `SEQ number`: 2000
	- `ACK number`: 101
3. 클라이언트 -> 서버
	- Flag: `ACK`
	- `SEQ number`: 101 (서버와 동기화 과정이 거쳐져서 서버 ACK 번호 사용)
	- `ACK number`: 2001
	- 동기화 적용 (3번째 요청) ACK, SYN 계산법
		- **보내는 쪽의 SEQ = 서버의 ACK**
		- **보내는 쪽의 ACK = 서버 SEQ + 1(뒤에 payload가 없기 때문에 1로 지정)**

## TCP 상태전이도
- TCP 연결 상태의 변화
	- `LISTEN`
		- 클라이언트의 연결 요청에 응답하도록 듣고 있는 상태
	- `ESTABLISHED`
		- 연결 수립 상태

## 실습
- TCP 3Way Handshake 과정 계산
- TCP 프로토콜 분석하기 