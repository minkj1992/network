# [CH08] 비연결지향형 UDP
- `사용자 데이터그램 프로토콜(UDP)`은 `Universal Datagram Protocol`이라 하기도한다.

## UDP 프로토콜
- UDP가 하는 일
	- 전송 방식이 단순하여 신뢰성이 낮다(`Datagram` 순서 변경, 중복, 통보 없이 누락)
	- **오류의 검사와 수정이 필요 없는** 프로그램에서 수행할 것으로  가정한다.
- UDP 프로토콜의 구조
	- `8bytes` = Source Port + Destination Port + Length + Checksum
## UDP 프로토콜을 사용하는 프로그램
- UDP 프로토콜을 사용하는 대표적인 프로그램
	- `DNS` 서버
	- `tftp` 서버: 파일 전송
	- `RIP` 프로토콜: 라우팅 정보를 공유(라우팅 테이블 공유)
## 실습
- `tftpd`를 사용하여 데이터 공유하기