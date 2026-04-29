# Oracle 11g Single Instance 설치 (Linux 6.8)


### 환경 구성
 
---
 
### 사용 소프트웨어
 
| 소프트웨어 | 버전 |
|-----------|------|
| VirtualBox | 7.2 |
| Oracle Enterprise Linux | 6.8 |
| Oracle Database | 11g Release 2 |
 
> 설치 파일 다운로드: [XE Prior Release Archive](https://www.oracle.com/database/technologies/xe-prior-release-downloads.html)
> - V100000-01_1of2.zip
> - V100000-01_2of2.zip
 
---
 
### 서버 구성
 
| VM 이름 | 호스트 이름 | 메모리 | 어댑터1 | 구성 방법 |
|---------|-----------|--------|--------|---------|
| oracle11g | ora11 | 8GB | 어댑터에 브리지 | 리눅스 설치 |
 
---
 
### 스토리지
 
| 파일 이름 | 용량 | 타입 | 용도 |
|----------|------|------|------|
| oracle11g.vdi | 50GB | Dynamic | 서버의 시스템 영역 |
 
---
 
### 네트워크
 
| VM | IP | Netmask | Gateway | DNS |
|----|-----|---------|---------|-----|
| oracle11g | 192.168.18.21 | 255.255.0.0 | 192.168.0.1 | 8.8.8.8 |
 
- Hostname: ora11
- Database name: orcl11g
---
 
### 1. VM 생성 및 기본 사양 설정
 
새로 만들기(New)로 VM을 생성한다.
 
- 이름: oracle11g
- 종류: Linux
- 버전: Oracle Linux (64-bit)
메모리 8GB, 프로세서 4개로 설정한다.
 
디스크는 50GB로 설정한다.
 
속성에서 포인팅 장치를 USB 태블릿으로 변경한다.
 
---
 
### 2. OS 설치 (Linux 6.8)
 
인스톨 전 테스트입니다. 테스트했다면 SKIP한다.
<img width="641" height="559" alt="image" src="https://github.com/user-attachments/assets/23541d1f-f180-4042-875a-a71943645be5" />

<img width="798" height="678" alt="image" src="https://github.com/user-attachments/assets/836e2d58-c979-40d9-a3af-f742e164702f" />
 
언어는 한국어로 선택한다.

<img width="795" height="680" alt="image" src="https://github.com/user-attachments/assets/53101762-185b-4aad-b52f-006d2bd188dc" />

<img width="789" height="683" alt="image" src="https://github.com/user-attachments/assets/356f1489-80cb-4a84-acab-e17d4736c774" />

<img width="788" height="673" alt="image" src="https://github.com/user-attachments/assets/d9d405eb-4c49-4139-b059-1973232cc9fb" />

<img width="789" height="678" alt="image" src="https://github.com/user-attachments/assets/bf3a6089-6af5-441b-affb-98a365c037ca" />

OS 호스트명과 네트워크 설정을 합니다. 어댑터에 브릿지 세팅이기에 사용할 수 있는 고유 IP로 세팅한다.

- 호스트명: ora11
- IP: 192.168.18.21
- 어댑터에 브리지 모드 설정

<img width="949" height="659" alt="image" src="https://github.com/user-attachments/assets/1ea2a114-5fc2-47db-a1ed-e0047b817627" />

<img width="796" height="682" alt="image" src="https://github.com/user-attachments/assets/963a7ea3-4014-4f5f-9ff6-a1d6731a0935" />

- root 암호: oracle
- oracle 유저 암호: oracle

<img width="792" height="672" alt="image" src="https://github.com/user-attachments/assets/f32dff63-eb8d-450d-baeb-a8b4340abf16" />

- Standard Partition 방식 선택
- swap: 기본 메모리의 절반 (약 4GB)
- /(root): 나머지 절반
- /app: 나머지 절반


<img width="791" height="679" alt="image" src="https://github.com/user-attachments/assets/8934605a-643d-4fe9-95cf-891bf128703e" />

<img width="795" height="679" alt="image" src="https://github.com/user-attachments/assets/4ff86cd2-4b51-47d5-b0c7-2d2f826966d9" />

<img width="950" height="676" alt="image" src="https://github.com/user-attachments/assets/7aafe52f-1bb0-4025-8ada-a41cc384eef7" />

오라클 설치를 위해 소프트웨어를 지금 선택하여 설치합니다.

<img width="954" height="680" alt="image" src="https://github.com/user-attachments/assets/b3d3fa7e-60ce-43e0-8bb8-ed666775698d" />

<img width="952" height="677" alt="image" src="https://github.com/user-attachments/assets/49c30439-74ee-4eff-8c91-cd737b128586" />

<img width="956" height="676" alt="image" src="https://github.com/user-attachments/assets/08d4be95-6744-44eb-932a-e3198eb60c44" />

설치 완료 후 리부트를 진행한다.

<img width="796" height="680" alt="image" src="https://github.com/user-attachments/assets/7a8c96d3-9b35-4cff-92bb-4e9d179840c1" />

<img width="789" height="673" alt="image" src="https://github.com/user-attachments/assets/446bd799-7187-4249-827f-d7a440880891" />

<img width="795" height="678" alt="image" src="https://github.com/user-attachments/assets/de75ce4e-c471-4aeb-b029-30f306cdaf52" />

<img width="791" height="676" alt="image" src="https://github.com/user-attachments/assets/d9c4a6e8-a597-4626-a28f-4da25ea62493" />

<img width="792" height="676" alt="image" src="https://github.com/user-attachments/assets/5f06514d-31a2-4feb-a4ef-2a99b66bfb16" />

<img width="797" height="680" alt="image" src="https://github.com/user-attachments/assets/c17c69d3-fee5-4a52-a191-2bf3652506c4" />

<img width="793" height="682" alt="image" src="https://github.com/user-attachments/assets/832a6675-4152-4dd3-a251-2094d146511b" />

예를 누르면 리부트를 진행합니다.

<img width="801" height="681" alt="image" src="https://github.com/user-attachments/assets/b6333e0d-e65d-4e38-840f-e6e6c65d1096" />

<img width="804" height="677" alt="image" src="https://github.com/user-attachments/assets/67d845fd-f27c-416c-adbe-80aa30cf964a" />

---
 
### 3. MobaXterm / PuTTY SSH 접속
 
리부트 완료 후 MobaXterm 또는 PuTTY로 SSH 접속한다.

<img width="892" height="598" alt="image" src="https://github.com/user-attachments/assets/ed351a04-ef08-4db5-ad84-f2cd8e02925f" />

<img width="549" height="269" alt="image" src="https://github.com/user-attachments/assets/31ec5739-915e-450a-bb83-65fc1f3cd3bf" />

 
```bash
# IP 확인
ifconfig
 
# 접속 정보
Host: 192.168.18.21
Port: 22
```
 
---
 
### 4. Oracle 설치 사전 환경 설정
 
root 유저로 아래 설정을 진행한다.
 
#### 호스트명 및 hosts 파일 설정
 
```bash
vi /etc/hosts
```
 
```
127.0.0.1   localhost
192.168.18.21 ora11
```
 
```bash
hostname ora11
vi /etc/sysconfig/network
# HOSTNAME=ora11
```
 
#### 커널 파라미터 설정
 
```bash
vi /etc/sysctl.conf
```
 
```
kernel.shmall = 2097152
kernel.shmmax = 536870912
kernel.shmmni = 4096
kernel.sem = 250 32000 100 128
net.ipv4.ip_local_port_range = 9000 65500
net.core.rmem_default = 262144
net.core.rmem_max = 4194304
net.core.wmem_default = 262144
net.core.wmem_max = 1048576
fs.aio-max-nr = 1048576
fs.file-max = 6815744
```
 
```bash
sysctl -p
```
 
#### limits 설정
 
```bash
vi /etc/security/limits.conf
```
 
```
oracle soft nproc 2047
oracle hard nproc 16384
oracle soft nofile 1024
oracle hard nofile 65536
oracle soft stack 10240
```
 
#### oracle 유저 및 그룹 생성
 
```bash
groupadd oinstall
groupadd dba
useradd -g oinstall -G dba oracle
passwd oracle
# 암호: oracle
```
 
#### 디렉터리 생성 및 권한 설정
 
```bash
mkdir -p /u01/app/oracle/product/11.2.0/dbhome_1
mkdir -p /u01/app/oraInventory
chown -R oracle:oinstall /u01
chmod -R 775 /u01
```
 
---
 
### 5. oracle 유저 환경변수 설정
 
```bash
su - oracle
vi ~/.bash_profile
```
 
```bash
export ORACLE_BASE=/u01/app/oracle
export ORACLE_HOME=/u01/app/oracle/product/11.2.0/dbhome_1
export ORACLE_SID=orcl11g
export TNS_ADMIN=$ORACLE_HOME/network/admin
export PATH=$PATH:$HOME/bin:$ORACLE_HOME/bin
export LD_LIBRARY_PATH=$ORACLE_HOME/lib:/lib:/usr/lib
export CLASSPATH=$ORACLE_HOME/JRE:$ORACLE_HOME/jlib:$ORACLE_HOME/rdbms/jlib
export PATH
```
 
```bash
source .bash_profile
```
 
---
 
### 6. 설치 파일 업로드 및 압축 해제
 
oracle 유저로 진행한다.
 
```bash
mkdir -p /tmp/install
cd /tmp/install
```
 
V100000-01_1of2.zip, V100000-01_2of2.zip 파일을 /tmp/install 경로에 업로드한 후 압축을 해제한다.
 
```bash
unzip V100000-01_1of2.zip -d /tmp/install
unzip V100000-01_2of2.zip -d /tmp/install
# 압축 해제 후 /tmp/install/database 디렉터리가 생성된다.
```
 
---
 
### 7. X11 환경 설정 (GUI 설치 준비)
 
Oracle Universal Installer는 GUI 환경에서 실행되므로 DISPLAY 환경변수를 설정한다.
 
```bash
echo $DISPLAY
 
# 값이 비어 있으면 아래와 같이 설정한다.
export DISPLAY=192.168.18.21:0.0
```
 
설치 프로그램 폰트 깨짐 방지를 위해 언어를 설정한다.
 
```bash
export LANG=en_US.UTF-8
export LANGUAGE=en_US.UTF-8
```
 
---
 
### 8. 설치 프로그램 실행
 
```bash
cd /tmp/install/database
./runInstaller
```

<img width="399" height="201" alt="image" src="https://github.com/user-attachments/assets/594dec33-571c-4769-8248-5669ad5cc902" />

설치 옵션은 아래 순서대로 진행한다.
 
| 단계 | 설정값 |
|------|--------|
| 설치 유형 | Install database software only |
| DB 유형 | Single instance database installation |
| 에디션 | Enterprise Edition |
| Oracle Base | /u01/app/oracle |
| Oracle Home | /u01/app/oracle/product/11.2.0/dbhome_1 |
| Inventory 경로 | /u01/app/oraInventory (그룹: oinstall) |
| OS 그룹 | dba |
| 비밀번호 | oracle |


<img width="794" height="629" alt="image" src="https://github.com/user-attachments/assets/09ca2de8-5509-4e6f-b3aa-59ad37303686" />

<img width="796" height="626" alt="image" src="https://github.com/user-attachments/assets/99c9908f-70bb-4e28-ac82-15b674667546" />

<img width="797" height="625" alt="image" src="https://github.com/user-attachments/assets/54bcb74c-4625-4055-bb17-176d314d31ca" />

<img width="787" height="625" alt="image" src="https://github.com/user-attachments/assets/3aaecddb-d9fc-4fbc-bb3e-46c342ed79ec" />

<img width="788" height="623" alt="image" src="https://github.com/user-attachments/assets/b9a2a62d-511c-438d-9cdb-de4dff90b311" />

<img width="800" height="626" alt="image" src="https://github.com/user-attachments/assets/52880fcf-abfb-475e-ab4a-bd6ed858445b" />

<img width="794" height="632" alt="image" src="https://github.com/user-attachments/assets/f56e0b91-cc1e-42ef-ab18-548bda4e4b30" />

---
 
### 9. root 스크립트 실행
 
설치 완료 직전 아래 스크립트를 root 유저로 실행한다.
 
```bash
/u01/app/oraInventory/orainstRoot.sh
/u01/app/oracle/product/11.2.0/dbhome_1/root.sh
```
 
실행 후 Enter를 눌러 기본값(/usr/local/bin)을 사용한다.

<img width="793" height="624" alt="image" src="https://github.com/user-attachments/assets/02a86f68-bbb8-4b1f-bb4b-2aaa76c0fa14" />

 
---
 
### 10. NetCA 실패 시 조치
 
설치 중 NetCA가 실패하더라도 설치 완료 후 아래와 같이 수동으로 리스너를 생성할 수 있다.

<img width="499" height="129" alt="image" src="https://github.com/user-attachments/assets/69213e97-ef32-4c13-aee7-e61ef433a666" />


```bash
$ORACLE_HOME/bin/netca
```
 
> NetCA 실패의 주요 원인은 아래와 같다.
> - /etc/hosts의 호스트명과 실제 IP가 불일치하는 경우
> - 환경변수와 DB 이름이 불일치하는 경우
> 설치 전에 호스트명과 환경변수를 반드시 통일해야 한다.

<img width="1218" height="514" alt="image" src="https://github.com/user-attachments/assets/b96f8056-d38f-474f-a371-af9f27a8be78" />

---
