# OSCP (OffSec Certified Professional) 자격증 가이드

인데 이제 아직 공부를 시작한 사람인 내가 찾아보고 알아본 내용들 틀린 점이나 부꿀 부분이 있다면 편히 바꿔주시길!

## 1. OSCP란 무엇인가?

![간지나죠잉](https://github.com/user-attachments/assets/21a2595f-789b-4169-a073-9e95c76120e3)

[Penetration Testing with Kali Linux (PEN-200)](https://portal.offsec.com/courses/pen-200-44065/overview)

**OSCP (Offensive Security Certified Professional)** 는 보안 업계에서 가장 인지도 높고 실무적인 모의해킹(Penetration Testing) 자격증입니다.

- 주관: OffSec

- 특징:

  - 100% 실기 시험: 객관식 문제가 전혀 없으며, 24시간 동안 실제 격리된 네트워크 환경에서 주어진 타겟 머신들을 해킹해야 합니다.

  - Try Harder: OffSec의 슬로건처럼 끈기와 집요한 문제 해결 능력을 요구합니다.

  - 공신력: 실무 능력을 증명하는 자격증으로 인정받아, 보안 관제나 모의해킹 컨설턴트 채용 시 우대받습니다.

## 2. 시험 구성 및 방식 (Exam Format)

시험은 총 **24시간의 해킹(실습)** 과 이후 24시간의 보고서 작성으로 이루어집니다.

### 2.1. 시험 환경 및 배점 (총 100점 만점 + 보너스 10점)

2025년 기준, 시험은 Active Directory(AD) 세트와 독립적인 타겟 머신들로 구성됩니다.


| 타겟 유형 (Target)   | 수량        | 배점 | 설명                                                                                            |
|----------------------|-------------|------|-------------------------------------------------------------------------------------------------|
| Active Directory Set | 1세트 (3대) | 40점 | DC(도메인 컨트롤러) 1대 + 클라이언트 2대.<br> 전체를 다 장악해야 점수 인정 (부분 점수 없음).       |
| Independent Targets  | 3대         | 60점 | 각각 독립된 리눅스/윈도우 머신 (각 20점).<br> User Flag(10점) + Root Flag(10점)으로 구성.          |
| Bonus Points         | 10점        | -    | PEN-200 코스 연습 문제(Topic Exercises) 80% 이상 완료 및  Lab 머신 30대 이상 해킹 시 획득 가능. |

### 2.2. 합격 기준

- 70점 이상 득점 시 합격입니다.

- 필수 조건: 획득한 플래그와 해킹 과정을 상세히 기록한 **침투 테스트 보고서(Penetration Test Report)** 를 제출해야 합니다. 점수가 넘더라도 보고서가 부실하면 불합격 처리됩니다.

## 3. 시험 범위 및 주요 내용 (PEN-200)

![많네..](https://github.com/user-attachments/assets/061f792a-eeb2-4bec-9e03-4e85b1d0dcdb)

OSCP 시험은 PEN-200 (Penetration Testing with Kali Linux) 교육 과정을 기반으로 출제됩니다.

### 3.1. 주요 학습 토픽

1. 정보 수집 (Information Gathering): Nmap, Recon-ng 등을 활용한 포트 스캔 및 서비스 식별.

2. 취약점 분석 (Vulnerability Analysis): 공개된 Exploit 검색 및 수정 (Searchsploit).

3. 웹 애플리케이션 공격: SQL Injection, XSS, RFI/LFI, Command Injection 등.

4. 클라이언트 사이드 공격: MS Office 매크로 등을 이용한 피싱 공격.

5. 공개된 익스플로잇 수정: C, Python 등으로 작성된 Exploit Code를 타겟 환경에 맞게 수정 및 컴파일.

6. 권한 상승 (Privilege Escalation):

   - Linux: Kernel Exploit, SUID/SGID, Cron Jobs, Misconfigurations.

   - Windows: Service Misconfigurations, DLL Hijacking, Unquoted Service Paths.

7. 포트 포워딩 및 터널링 (Pivoting): 외부에서 접근 불가능한 내부 네트워크로 침투 (Proxychains, SSH Tunneling).

8. Active Directory (AD): Kerberoasting, AS-REP Roasting, Golden Ticket, BloodHound 활용 등.

## 4. 응시 비용 및 패키지 (Pricing 2025)

![키에엑 비싸다](https://github.com/user-attachments/assets/511683b7-c765-4920-9195-0de7db83468e)

OffSec의 가격 정책은 변동될 수 있으나, 일반적으로 아래 두 가지 옵션이 가장 많이 선택됩니다. (환율에 따라 변동)

[offsec/pen-200](https://www.offsec.com/courses/pen-200/) 공식은 여기로

| 패키지명             | 가격 (USD) | 포함 내용                                                                                           | 비고                                                |
|----------------------|------------|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------|
| Course + certification Exam Bundle | $1,749     | - PEN-200 코스 자료 (90일)  <br> - 90일 Lab 접속 권한 <br>  - 시험 응시권 1회                             | 가장 기본적인 패키지.    기간 내 집중 학습 필요.    |
| Learn One            | $2,749     | - PEN-200 코스 자료 (1년) <br>  - 1년 Lab 접속 권한 <br>  - 시험 응시권 2회  <br> - PEN-103/210 등 추가 코스 | 직장인이나 장기 준비생 추천.    재시험 부담이 적음. |
| 재시험 비용 (Retake) | $249       | - 시험 응시권 1회 추가                                                                              | 불합격 시 추가 결제 비용.                           |

참고: 2025년 기준 OSCP+ 도입 등에 따라 프로모션이나 가격 정책이 바뀔 수 있으므로, 결제 전 OffSec 공식 홈페이지를 반드시 확인하세요.

## 5. 준비 과정 및 팁 (Roadmap)

### Step 1: 기초 다지기

- 리눅스/윈도우 기본 명령어 숙지.

- 네트워크 기초 (TCP/IP, HTTP, DNS 등) 이해.

- 프로그래밍 기초 (Python, Bash): 스크립트를 읽고 수정할 수 있는 수준.

### Step 2: 실전 연습 (Hands-on)

- Hack The Box (HTB): 'TJ Null’s OSCP List'에 있는 머신들을 집중 공략.

- TryHackMe: 'Offensive Pentesting' 패스 추천.

- Proving Grounds (PG): OffSec에서 운영하는 연습 플랫폼으로, 실제 시험과 가장 유사한 환경 제공.

### Step 3: PEN-200 코스 수강

- 제공되는 PDF/영상 교재 학습.

- Lab 환경에 접속하여 다양한 시나리오 실습.

- Topic Exercises를 풀어 보너스 점수(10점) 확보.

### Step 4: 모의 보고서 작성

- 연습한 머신에 대해 실제 시험처럼 리포트를 써보는 연습 필수.

- 스크린샷 찍는 습관 들이기 (whoami, ipconfig, type proof.txt).

## 6. 자주 묻는 질문 (FAQ)

> Q. 코딩을 잘해야 하나요?

A. 개발자 수준의 코딩 능력은 필요 없지만, 남이 짠 Python/Bash/C 코드를 읽고 내 IP나 포트에 맞게 수정할 수 있는 능력은 필수입니다.

> Q. 메타스플로잇(Metasploit) 쓸 수 있나요?

A. 제한적으로 가능합니다. 시험 전체에서 단 1대의 머신에만 Metasploit(Meterpreter 등) 사용이 허용됩니다. 나머지는 수동으로 익스플로잇해야 합니다. (단, multi/handler나 msfvenom은 제한 없이 사용 가능)

> Q. Active Directory(AD)가 어렵나요?

A. 최근 시험에서 AD의 비중(40점)이 매우 커졌습니다. AD 한 세트를 못 뚫으면 합격이 사실상 불가능하므로, Pivoting과 AD 공격 기법을 철저히 준비해야 합니다.