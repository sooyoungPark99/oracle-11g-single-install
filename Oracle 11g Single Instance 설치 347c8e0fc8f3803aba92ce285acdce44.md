# Oracle 11g Single Instance 설치

## 설치 방식

본 가이드는 교육용으로 제공된 OVA 이미지를 VirtualBox에 가져와서
Oracle 11g 환경을 구성하는 방식으로 진행했습니다.

- OVA 이미지: 교육 과정에서 제공된 사전 구성 이미지 사용
- Oracle 11g 공식 설치 파일:
[https://www.oracle.com/database/technologies/oracle-database-software-downloads.html](https://www.oracle.com/database/technologies/oracle-database-software-downloads.html)

---

## 1) 11g 이미지 준비 및 가져오기

1. 11gWS2.ova 이미지 파일을 로컬 디스크에 준비한다.

![image.png](image.png)

1. VirtualBox 상단 메뉴에서 파일 → 가상 시스템 가져오기를 선택한다.

![image.png](image%201.png)

 D:\11g\11gWS2.ova 파일을 선택하여 가져오기를 진행한다.

![image.png](80a6f1e9-b3c8-4c6c-ae16-5b5df0b35ff8.png)

가져올 VM 설정을 확인한다.

![image.png](ab34043d-f7d6-4b0b-b6c5-cf153e01c7af.png)

가져오기 완료 후 VM을 실행했으나 오류가 발생하여 중지 후 설정을 수정한다.

![image.png](image%202.png)

#### VM 설정 수정 - 프로세서

VM을 중지 후 설정에서 프로세서를 CPU 1개로 변경
→ 마더보드 탭에서 I/O APIC 활성화를 체크 해제하여 부팅 오류를 해결했다.

![image.png](1a0d3299-3b05-4f70-b3ab-28a1348167a4.png)

플로피 디스크 해제, 포인팅 장치 (USB 태블릿) 으로 설정한다.

![image.png](2c64d4ff-ece6-48b1-bfd6-71366cf7523a.png)

리눅스를 시작한다.

![image.png](image%203.png)

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

#### 네트워크 설정 확인

1. TCP 프로토콜로 호스트 IP 192.168.13.31, 호스트 포트 8081, 게스트 IP 10.0.2.129, 게스트 포트 1521로 설정
2. Windows ipconfig로 호스트 IP(192.168.13.31), 서브넷 마스크(255.255.0.0), 게이트웨이(192.168.0.1)를 확인한다.

![image.png](image%204.png)

 ****

**DB 접속 및 사용자 계정 활성화**

oracle 유저로 전환 후 sqlplus로 DB 접속을 확인했다.

![image.png](image%205.png)