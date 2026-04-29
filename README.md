# Oracle 11g Single Instance 설치 (Linux 6.8)
 
Oracle Enterprise Linux 6.8 환경에서 Oracle 11g Release 2 Single Instance 설치 가이드입니다.
 
---
 
#### 환경 구성
 
| 항목 | 내용 |
|------|------|
| OS | Oracle Enterprise Linux 6.8 |
| DB 버전 | Oracle Database 11g Release 2 |
| DB 이름 | orcl11g |
| 가상화 | VirtualBox 7.2 |
| 메모리 | 8GB |
| CPU | 4Core |
 
---
 
#### 서버 구성
 
| VM 이름 | 호스트 이름 | IP | 넷마스크 | 게이트웨이 | DNS |
|---------|-----------|-----|---------|----------|-----|
| oracle11g | ora11 | 192.168.18.21 | 255.255.0.0 | 192.168.0.1 | 8.8.8.8 |
 
---
 
#### 설치 파일
 
- [Oracle 11g 설치 파일 다운로드](https://www.oracle.com/database/technologies/xe-prior-release-downloads.html)
  - V100000-01_1of2.zip
  - V100000-01_2of2.zip
---
 
#### 설치 순서
 
| 순서 | 내용 |
|------|------|
| 1 | VM 생성 및 기본 사양 설정 |
| 2 | Oracle Linux 6.8 설치 |
| 3 | MobaXterm / PuTTY SSH 접속 |
| 4 | Oracle 설치 사전 환경 설정 |
| 5 | oracle 유저 환경변수 설정 |
| 6 | 설치 파일 업로드 및 압축 해제 |
| 7 | X11 환경 설정 |
| 8 | runInstaller 실행 |
| 9 | root 스크립트 실행 |
| 10 | DB 생성 (DBCA) |
 
---
 
#### 주요 특징
 
- Oracle Enterprise Linux 6.8 기반 실습 환경 구성
- Standard Partition 방식으로 스토리지 구성
- X11 Forwarding을 활용한 GUI 설치 환경 구성
- NetCA 실패 시 수동 리스너 생성 방법 포함
- 실제 설치 중 발생한 오류 및 해결 방법 포함
