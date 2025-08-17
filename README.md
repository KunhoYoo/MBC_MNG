# 📡 MBC MNG 현황판

MNG 장비의 **불출/반납 현황 관리**를 위한 웹 기반 현황판입니다.  
Firebase Realtime Database 를 백엔드로 사용하며, 현황판 UI, 불출 등록, 로그 기록/다운로드 등의 기능을 제공합니다.

---

## 🚀 주요 기능

### 1. 로그인
- **코드 기반 로그인**: 사용자별 고유 코드 입력 시 자동으로 이름이 매핑됩니다.
- 로그인 후 **현황 모드** 또는 **불출 모드** 선택 진입.

### 2. 현황판 (Status Page)
- 모든 MNG 장비의 상태를 **실시간 테이블**로 확인 가능.
- 장비별 상태:
  - `사용자`
  - `불출자`
  - `위치`
  - `반납 여부`
- **반납 버튼(⟲)** 클릭 시 해당 장비 초기화.

#### ⏱ 시간 표시
- PC 버전에서 로고 우측에 표시:
  - **현재 시간** (실시간 1초 갱신)
  - **최근 업데이트 시간** (마지막 알림 기준)

### 3. 불출 등록 (Issue Page)
- 장비 선택 후 사용자/위치 입력 → **불출 처리**.
- 입력 시 기록이 Firebase DB에 즉시 반영.

### 4. 로그 관리 (Log Modal)
- 상단 `Log` 버튼 클릭 시 최근 **20개 불출/반납 기록** 모달 표시.
- **텍스트 다운로드**:
  - 현재 로그를 `.txt` 파일로 내려받기 가능.
- **Log 전체 삭제**:
  - 관리자 전용 기능.
  - 비밀번호 입력(`mbcmngreset`) 시 모든 로그 및 히스토리 초기화.
  - Firebase `globalLog`, `mngHistory`, `lastIssue`, `lastReturn` 전부 초기화.
  - 로컬 상태도 초기화되어 **즉시 반영**됨.

### 5. 알림 (Toast)
- 새로운 불출/반납 발생 시 화면 우측 하단에 **알림 Toast** 표시.
- 알림 시 **효과음(alarm.mp3)** 재생.

### 6. Firebase 연동
- `Realtime Database`와 실시간 연동:
  - `mngData` : 현황 데이터
  - `mngHistory` : 장비별 과거 기록 (최대 5개 저장)
  - `globalLog` : 전역 불출/반납 로그 (최대 500개 저장)
  - `lastIssue`, `lastReturn` : 가장 최근 이벤트 기록

---

## 🖥 지원 환경
- **데스크톱 (PC)**: 전체 기능 지원
- **모바일**: UI 단순화 (예: 시간 표시 숨김)

---

## ⚡ 기술 스택
- **Frontend**: HTML, CSS, JavaScript (Vanilla)
- **Backend(DB)**: Firebase Realtime Database
- **Deploy**: 정적 호스팅 가능 (Firebase Hosting, GitHub Pages 등)
https://kunhoyoo.github.io/MBC_MNG/
