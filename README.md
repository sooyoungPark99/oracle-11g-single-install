# Oracle 11g Single Instance 설치

교육 과정에서 제공된 OVA 이미지를 VirtualBox에 가져와
Oracle 11g 환경을 구성하는 방식으로 진행했습니다.

- OVA 이미지: 교육 과정에서 제공된 사전 구성 이미지 사용
- Oracle 11g 공식 설치 파일:
  https://www.oracle.com/database/technologies/oracle-database-software-downloads.html

---

### 환경 구성

| 항목 | 내용 |
|------|------|
| OS | Oracle Linux (32-bit) |
| DB 버전 | Oracle Database 11g Release 2 (11.2.0.1.0) |
| 가상화 | VirtualBox 7.0.18 |
| CPU | 1Core |
| 메모리 | 2048MB |

---

### 설치 가이드

- [Oracle 11g Single Instance 설치](./Oracle%2011g%20Single%20Instance%20%EC%84%A4%EC%B9%98.md)

---

### 주요 작업 내용

- OVA 이미지를 VirtualBox에 가져와 VM 환경 구성
- CPU 1개, I/O APIC 설정 수정으로 부팅 오류 해결
- 포트 포워딩 설정으로 호스트-게스트 간 네트워크 연결 구성
- sqlplus를 통한 DB 접속 확인
- HR, SH 계정 잠금 해제 및 비밀번호 재설정


