#### (샘플_요구사항 분석서 파일을 충실히 참고하였습니다)

# 요구사항 분석서 ( 주차를 왕처럼 편하게, King Parking )

---

# 목차

## 1. 서론
- 1.1 목적 및 범위
- 1.2 용어 정의
- 1.3 참조 문서

## 2. 시스템 개요
- 2.1 소프트웨어 컨텍스트(Context)
- 2.2 기능 분류 및 설명

## 3. 요구사항 명세
- 3.1 정적 분석
- 3.2 CRC 카드
- 3.3 동적 분석

## 4. 인터페이스 분석

## 5. 제약사항

## 6. 요구사항 추적표

## 7. 참고문헌 및 부록

---

# 1. 서론

## 1.1 목적 및 범위

본 문서는 King Parking 시스템의 요구사항을 분석하고 정의하기 위한 문서이다.

King Parking은 사용자와 주차장을 연결하여 주차 공간을 효율적으로 관리할 수 있도록 지원하는 온라인 주차 관리 시스템이다.

본 문서는 기능적 요구사항, 비기능적 요구사항, 인터페이스 요구사항을 기반으로 시스템 구조와 동작을 분석하는 것을 목적으로 한다.

또한 시스템 구현 이전 단계에서 필요한 모델링 및 요구사항 관계를 정의하여 개발 과정의 기준 문서로 활용한다.

---

## 1.2 용어 정의

| 용어 | 설명 |
|---|---|
| 사용자 | 주차장을 이용하는 일반 회원 |
| 관리자 | 주차장을 등록 및 관리하는 사용자 |
| 예약 | 특정 시간 동안 주차 공간을 확보하는 행위 |
| 결제 | 주차 공간 이용 요금을 지불하는 과정 |
| 실시간 주차 현황 | 현재 주차 가능한 공간 정보를 제공하는 기능 |
| 알림 | 예약 시간 및 종료 시간을 알려주는 기능 |

---

## 1.3 참조 문서

- [King Parking] 프로젝트 관리 계획서
- [King Parking] 요구사항 정의서
- [King Parking] 품질 요소 측정 문서

---

# 2. 시스템 개요

## 2.1 소프트웨어 컨텍스트(Context)

### 2.1.1 Actor Table

| Actor | Role |
|---|---|
| 사용자 | 주차장을 검색하고 예약 및 결제를 수행하는 사용자 |
| 관리자 | 주차장을 등록 및 관리하는 사용자 |
| 시스템 | 예약, 결제, 알림 기능을 처리하는 시스템 |
| 외부 결제 API | 결제 서비스를 제공하는 외부 시스템 |
| 지도 API | 주차장 위치 정보를 제공하는 외부 시스템 |

---

### 2.1.2 Use Case Diagram

<img width="880" height="636" alt="image" src="https://github.com/user-attachments/assets/fc396de4-8b60-4641-8e33-00ee1aa2195d" />

---

## 2.2 기능 분류 및 설명

---

# 2.2.1 UseCase Description

---

## Use Case Name : 회원가입을 한다.
- ID : U_01
- Importance Level : High

### Primary Actor
사용자

### Brief Description
사용자가 이메일과 비밀번호를 입력하여 회원가입을 수행한다.

### Trigger
사용자가 회원가입 버튼을 누른다.

### Normal Flow of Events

1. 사용자는 이메일과 비밀번호를 입력한다.
2. 사용자는 회원가입 버튼을 누른다.
3. 시스템은 회원 정보를 저장한다.
4. 시스템은 회원가입 완료 메시지를 출력한다.

### Alternate / Exceptional Flows

- 이메일 형식이 올바르지 않을 경우 오류 메시지를 출력한다.
- 이미 가입된 이메일일 경우 회원가입 실패 메시지를 출력한다.

---

## Use Case Name : 로그인을 한다.
- ID : U_02
- Importance Level : High

### Primary Actor
사용자

### Brief Description
사용자가 로그인 기능을 수행한다.

### Trigger
사용자가 로그인 버튼을 누른다.

### Normal Flow of Events

1. 사용자는 이메일과 비밀번호를 입력한다.
2. 시스템은 회원 정보를 검증한다.
3. 로그인 성공 시 메인 화면으로 이동한다.

### Alternate / Exceptional Flows

- 비밀번호가 일치하지 않으면 로그인 실패 메시지를 출력한다.

---

## Use Case Name : 주차장을 등록한다.
- ID : U_03
- Importance Level : High

### Primary Actor
관리자

### Brief Description
관리자가 주차장 정보를 등록한다.

### Trigger
관리자가 등록 버튼을 누른다.

### Normal Flow of Events

1. 관리자는 주차장 위치, 요금, 공간 수를 입력한다.
2. 등록 버튼을 누른다.
3. 시스템은 주차장 정보를 저장한다.

### Alternate / Exceptional Flows

- 입력값이 비어 있을 경우 등록 실패 메시지를 출력한다.

---

## Use Case Name : 주차장을 수정한다.
- ID : U_04

### Primary Actor 
관리자

### Normal Flow of Events

1. 관리자는 수정할 주차장을 선택한다.
2. 관리자는 수정 정보를 입력한다.
3. 시스템은 수정 내용을 저장한다.

--- 

## Use Case Name : 주차장을 삭제한다.
- ID : U_05

### Primary Actor 
관리자

### Normal Flow of Events

1. 관리자는 삭제할 주차장을 선택한다.
2. 시스템은 주차장 정보를 삭제한다.

---

## Use Case Name : 주차장을 검색한다.
- ID : U_06
- Importance Level : High

### Primary Actor
사용자

### Brief Description
사용자가 원하는 주차장을 검색한다.

### Trigger
사용자가 검색 버튼을 누른다.

### Normal Flow of Events

1. 사용자는 위치 기반 검색을 수행한다.
2. 시스템은 주변 주차장 목록을 출력한다.
3. 사용자는 상세 정보를 확인한다.

---

## Use Case Name : 주차 공간을 예약한다.
- ID : U_07
- Importance Level : High

### Primary Actor
사용자

### Brief Description
사용자가 원하는 시간에 주차 공간을 예약한다.

### Trigger
사용자가 예약 버튼을 누른다.

### Normal Flow of Events

1. 사용자는 원하는 주차장을 선택한다.
2. 예약 시간과 차량 정보를 입력한다.
3. 예약 버튼을 누른다.
4. 시스템은 예약 정보를 저장한다.

### Alternate / Exceptional Flows

- 예약 가능한 공간이 없을 경우 예약 실패 메시지를 출력한다.

---

## Use Case Name : 예약 조회를 한다.
- ID : U_08

### Primary Actor 
사용자

### Normal Flow of Events

1. 사용자는 예약 조회 버튼을 누른다.
2. 시스템은 예약 목록을 출력한다.
   
---

## Use Case Name : 예약을 취소한다.
- ID : U_09

### Primary Actor 
사용자

### Normal Flow of Events

1. 사용자는 예약 취소 버튼을 누른다.
2. 시스템은 예약 정보를 삭제한다.
3. 시스템은 취소 완료 메시지를 출력한다.

---

## Use Case Name : 결제를 수행한다.
- ID : U_10
- Importance Level : High

### Primary Actor
사용자

### Brief Description
사용자가 주차 요금을 결제한다.

### Trigger
사용자가 결제 버튼을 누른다.

### Normal Flow of Events

1. 사용자는 결제 수단을 선택한다.
2. 시스템은 외부 결제 API를 호출한다.
3. 결제가 완료되면 이용 내역을 저장한다.

### Alternate / Exceptional Flows

- 결제 실패 시 오류 메시지를 출력한다.

---

## Use Case Name : 실시간 주차 현황을 조회한다.
- ID : U_11
- Importance Level : High

### Primary Actor
사용자

### Brief Description
사용자가 실시간 주차 가능 공간을 조회한다.

### Trigger
사용자가 주차장을 선택한다.

### Normal Flow of Events

1. 사용자는 주차장을 선택한다.
2. 시스템은 현재 주차 가능 공간 수를 출력한다.

---

## Use Case Name : 알림을 전송한다.
- ID : U_12
- Importance Level : Medium

### Primary Actor
시스템

### Brief Description
시스템이 예약 및 종료 알림을 전송한다.

### Trigger
예약 시간 도래 또는 종료 시간 임박

### Normal Flow of Events

1. 시스템은 예약 시간을 확인한다.
2. 사용자에게 예약 알림을 전송한다.
3. 종료 시간이 가까워질 경우 추가 알림을 전송한다.

---

# 3. 요구사항 명세

## 3.1 정적 분석

<img width="462" height="647" alt="image" src="https://github.com/user-attachments/assets/8845a5aa-262b-44e0-92c4-d23b84678119" />

---

## 3.2 CRC 카드

---

## Class Name : 사용자
- ID : 01
- Type : Concrete, Domain

### Description
주차장을 예약하고 이용하는 회원을 나타낸다.

### Associated Use Case
- U_01
- U_02
- U_08
- U_09

### Responsibilities
- 회원가입 요청
- 로그인 요청
- 예약 요청
- 예약 조회

### Collaborators
- 예약
- 결제
- 알림

### Attributes
- 사용자 ID : Integer
- 이메일 : String
- 비밀번호 : String

---

## Class Name : 관리자
- ID : 02

### Description
주차장을 등록 및 관리하는 관리자를 나타낸다.

### Responsibilities
- 주차장 등록
- 주차장 수정
- 주차장 삭제

### Collaborators
- 주차장

### Attributes
- 관리자 ID
- 이메일
- 비밀번호

---

## Class Name : 주차장
- ID : 03

### Responsibilities
- 주차 공간 관리
- 실시간 현황 제공

### Attributes
- 주차장 ID
- 위치
- 요금
- 주차 가능 공간 수

---

## Class Name : 예약
- ID : 04

### Responsibilities
- 예약 저장
- 예약 취소
- 예약 조회

### Attributes
- 예약 ID
- 예약 시간
- 차량 번호

---

## Class Name : 결제
- ID : 05

### Responsibilities
- 결제 처리
- 결제 내역 저장

### Collaborators
- 외부 결제 API

---

## Class Name : 알림
- ID : 06

### Responsibilities
- 예약 알림 전송
- 종료 알림 전송

---

## 3.3 동적 분석

#### 3.3.1 회원가입을 한다.
<img width="547" height="388" alt="image" src="https://github.com/user-attachments/assets/0cb63667-e6ed-467f-8787-7a304be2b421" />

#### 3.3.2 로그인을 한다.
<img width="547" height="390" alt="image" src="https://github.com/user-attachments/assets/cb9a50f3-d5bd-4505-975a-9042472b6062" />

#### 3.3.3 주차장을 등록한다.
<img width="547" height="386" alt="image" src="https://github.com/user-attachments/assets/948de3a1-7968-40d7-acab-1afae958e419" />

#### 3.3.4 예약을 한다.
<img width="547" height="392" alt="image" src="https://github.com/user-attachments/assets/9f586005-70b2-44cf-9ede-5d96e76a2c95" />

#### 3.3.5 결제를 한다.
<img width="545" height="390" alt="image" src="https://github.com/user-attachments/assets/be9ebf36-80fd-42f3-a042-e1e8015fea0a" />

#### 3.3.6 알림을 전송한다.
<img width="546" height="386" alt="image" src="https://github.com/user-attachments/assets/23cd1961-7c41-4ead-9b89-0c862407c723" />

---

# 4. 인터페이스 분석

| 인터페이스 | 설명 |
|---|---|
| 지도 API | 주차장 위치 표시 |
| 결제 API | 결제 처리 |
| 알림 API | 예약 및 종료 알림 전송 |

---

# 5. 제약사항

| ID | 제약사항 |
|---|---|
| CR-001 | 개인정보 보호법을 준수해야 한다. |
| CR-002 | 결제 정보는 암호화되어야 한다. |
| CR-003 | 시스템은 웹 및 모바일 환경을 지원해야 한다. |

---

# 6. 요구사항 추적표

| 요구사항 | U_01 | U_02 | U_03 | U_04 | U_05 | U_06 | U_07 | U_08 | U_09 | U_10 | U_11 | U_12 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| FR-001 | O |  |  |  |  |  |  |  |  |  |  |  |
| FR-002 |  | O |  |  |  |  |  |  |  |  |  |  |
| FR-003 |  | O |  |  |  |  |  |  |  |  |  |  |
| FR-004 |  |  | O |  |  |  |  |  |  |  |  |  |
| FR-005 |  |  |  | O | O |  |  |  |  |  |  |  |
| FR-006 |  |  | O | O | O |  |  |  |  |  |  |  |
| FR-007 |  |  |  |  |  | O |  |  |  |  |  |  |
| FR-008 |  |  |  |  |  | O |  |  |  |  | O |  |
| FR-009 |  |  |  |  |  |  | O |  |  |  |  |  |
| FR-010 |  |  |  |  |  |  |  | O |  |  |  |  |
| FR-011 |  |  |  |  |  |  |  |  | O |  |  |  |
| FR-012 |  |  |  |  |  |  |  |  |  | O |  |  |
| FR-013 |  |  |  |  |  |  |  |  |  | O |  |  |
| FR-014 |  |  |  |  |  |  |  |  |  |  |  | O |

---

# 7. 참고문헌 및 부록

- King Parking 프로젝트 관리 계획서
- King Parking 요구사항 정의서
- King Parking 품질 요소 측정 문서
- 샘플 요구사항분석서
- draw.io 이용 
