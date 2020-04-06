# [CH11] 7계층 프로토콜 HTTP

## HTTP 프로토콜
- 웹을 만드는 기술들
- HTTP 프로토콜의 특징
	- `HTTP 1.0`의 특징
		- 연결 수립, 동작, 해제의 단순함
			- 하나의 URL은 하나의 TCP 연결
		- HTML 문서를 전송 받은 뒤 연결을 끊고 다시 연결하여 데이터를 전송한다.
		- **단순 동작이 반복되어 통신 부하 문제** (요청/응답 1당 3way hand shake 1번)
	- `HTTP 1.1`
		- 위의 연결 문제를 전달할 데이터 다 받은 뒤, 소켓 연결 끊도록 해결
- HTTP 프로토콜의 통신과정

## HTTP 요청 프로토콜
- 프로토콜의 구조
	- 1. `Request Line`
		- `HTTP Method` + 공백 + `URI` + 공백 + HTTP 버전
	- 2. `Headers`: 옵션들
	- 3. `공백`
	- 4. `Body` 데이터들
- 요청 타입(HTTP Method)
	- Get
	- POST
	- ....
- URI
	- Uniform Resource Identifier
	- `scheme ://host[:port][/path][?query]`
	- ex) ftp	://IP주소 :포트주소/파일이름?name="code"
	- 위의 IP주소/포트주소 --> 도메인 주소로 대체할 수 있다.
	- 컴퓨터가 DNS 서버를 통해서 IP를 매핑하는 룩업테이블을 가지고 있기 때문
	- 포트번호는 well-known 포트로 생략되었있는것 (네이버의 경우, `.:443`)
## HTTP 응답 프로토콜
- 프로토콜의 구조
- 상태 코드
## HTTP 헤더 포맷
- HTTP 헤더 구조
- 일반 헤더
- 요청 헤더
- 응답 헤더
## 실습
- HTTP 작성
- HTTP 수정