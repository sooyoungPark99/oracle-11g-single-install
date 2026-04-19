# Oracle 11g Single Instance 설치


### 1. 11g 이미지 준비 및 가져오기

11gWS2.ova 이미지 파일을 로컬 디스크에 준비한다.

<img width="1544" height="558" alt="image" src="https://github.com/user-attachments/assets/931c323e-d254-48e4-af15-f007a1340bd3" />

VirtualBox 상단 메뉴에서 파일 → 가상 시스템 가져오기를 선택한다.

<img width="1748" height="569" alt="image" src="https://github.com/user-attachments/assets/be712242-6ea3-4ea9-b490-fdc71150e92d" />

D:\11g\11gWS2.ova 파일을 선택하여 가져오기를 진행한다.

<img width="645" height="468" alt="image" src="https://github.com/user-attachments/assets/612af452-96c1-4b62-b77d-f23c2459600d" />

가져올 VM 설정을 확인한다.

<img width="646" height="474" alt="image" src="https://github.com/user-attachments/assets/4dbd87ff-c57d-4005-966a-36772a4b5b9f" />

가져오기 완료 후 VM을 실행했으나 오류가 발생하여 중지 후 설정을 수정한다.

<img width="1891" height="375" alt="image" src="https://github.com/user-attachments/assets/94182715-6635-4e37-bd89-fe70f81bd30f" />

#### 2. VM 설정 수정(프로세서/부팅 오류)

VM을 중지 후 설정에서 프로세서를 CPU 1개로 변경
→ 마더보드 탭에서 I/O APIC 활성화를 체크 해제하여 부팅 오류를 해결했다.

<img width="767" height="509" alt="image" src="https://github.com/user-attachments/assets/5aba6858-f5be-482b-bd32-72e9d3239dce" />

플로피 디스크 해제, 포인팅 장치 (USB 태블릿) 으로 설정한다.

<img width="766" height="512" alt="image" src="https://github.com/user-attachments/assets/1c199cda-99ed-4f07-9e98-2600aca1f624" />

#### DB 접속 및 사용자 계정 활성화

<img width="1277" height="795" alt="image" src="https://github.com/user-attachments/assets/8867c9a9-1c7a-4d9c-a1c0-5d8ca25fb55e" />

- oracle 유저로 전환 후 sqlplus로 DB 접속을 확인한다.
- HR, SH 계정의 잠금을 해제하고 비밀번호를 재설정해준다.

```sql
[root@edydr1p0 ~]# su - oracle
[orcl:~]$
[orcl:~]$
[orcl:~]$ sqlplus / as sysdba

SQL*Plus: Release 11.2.0.1.0 Production on Fri Feb 27 11:59:44 2026

Copyright (c) 1982, 2009, Oracle.  All rights reserved.

Connected to:
Oracle Database 11g Enterprise Edition Release 11.2.0.1.0 - Production
With the Partitioning, Automatic Storage Management, OLAP, Data Mining
and Real Application Testing options

SQL> alter user hr
  2   account unlock;

User altered.

SQL> alter user hr
  2   identified by hr;

User altered.

SQL> alter user sh
  2   account unlock;

User altered.

SQL> alter user sh
  2  identified by sh;

User altered.

SQL> connect sh/sh
Connected.
SQL>
SQL> select table_name, num_rows
  2   from user_tables;

TABLE_NAME                       NUM_ROWS
------------------------------ ----------
DIMENSION_EXCEPTIONS                    0
SALES                              918843
COSTS                               82112
DR$SUP_TEXT_IDX$K
DR$SUP_TEXT_IDX$N
SALES_TRANSACTIONS_EXT                  0
SUPPLEMENTARY_DEMOGRAPHICS           4500
CAL_MONTH_SALES_MV                     48
FWEEK_PSCAT_SALES_MV                11266
CHANNELS                                5
CUSTOMERS                           55500

TABLE_NAME                       NUM_ROWS
------------------------------ ----------
COUNTRIES                              23
TIMES                                1826
DR$SUP_TEXT_IDX$R
PRODUCTS                               72
PROMOTIONS                            503
DR$SUP_TEXT_IDX$I

17 rows selected.

```

### 3. 네트워크 설정 확인

1. TCP 프로토콜로 호스트 IP 192.168.13.31, 호스트 포트 8081, 게스트 IP 10.0.2.129, 게스트 포트 1521로 설정
2. Windows ipconfig로 호스트 IP(192.168.13.31), 서브넷 마스크(255.255.0.0), 게이트웨이(192.168.0.1)를 확인한다.

<img width="1092" height="829" alt="image" src="https://github.com/user-attachments/assets/0bb81088-70ee-4f92-872c-5439d1c043e9" />

### 4. DB 접속 및 사용자 계정 활성화

oracle 유저로 전환 후 sqlplus로 DB 접속을 확인했다.

<img width="762" height="547" alt="image" src="https://github.com/user-attachments/assets/f8af7c1c-f595-4019-8e66-18af80da7718" />
