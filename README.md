# Artnex MariaDB Schema

이 저장소에는 **퍼스널 컬러 & 브랜드 진단 서비스**에서 사용하는 MariaDB 스키마와 샘플 데이터(`artnex.sql`)가 포함되어 있습니다.  
HeidiSQL을 통해 localhost 환경에서 추출된 덤프 파일을 버전 관리하고 있습니다.

---

## 📂 Database 개요
- **Database:** `artnex`  

### 🗂️ Tables

#### 1. style_toolkits (22 rows)
브랜드/퍼스널 컬러 **22가지 스타일 아키타입** 정의  
- **컬럼**
  - `style_name` (VARCHAR, PK) → 스타일 이름 (예: Cute, Romantic, Noble 등 22개 유형)
  - `palette_hex` (VARCHAR) → HEX 색상 팔레트 배열
  - `fonts` (VARCHAR) → 추천 폰트
  - `materials` (VARCHAR) → 어울리는 소재/마감
  - `scent_music` (TEXT) → 향/음악 키워드
  - `updated_at` (DATETIME) → 최종 수정 일시
- **내용:** 시각·감각 자원(색상, 폰트, 소재, 향/음악)을 포함한 스타일별 툴킷 데이터

#### 2. question_bank (148 rows)
퍼스널 컬러 & 브랜드 진단 **질문 데이터**  
- **컬럼**
  - `id` (VARCHAR, PK) → 문항 ID (Q1, Q2A, Q10D 등)
  - `prompt` (TEXT) → 질문 텍스트
  - `answers_str` (TEXT) → 답변 목록 및 deltas(JSON 형태: hue, value, chroma, contrast)
  - `next_map_str` (TEXT) → 다음 질문 분기 매핑
  - `adaptive_axis` (ENUM) → 분기 축 (hue / value / chroma / contrast)
  - `version` (VARCHAR) → 문항/스키마 버전
  - `updated_at` (DATETIME) → 최종 갱신 시각
  - `answer_key` (CHAR) → 보기 키 (1~4)
  - `order_no` (INT) → 문항 순서
- **내용:**  
  - 10개 메인 질문(Q1~Q10)  
  - 하위 분기 문항(Q2A~Q10D 포함)  
  - 총 **148개 질문**과 답변 데이터  

---

## ⚙️ 사용 방법

### 1. 데이터베이스 생성
```sql
CREATE DATABASE artnex 
  CHARACTER SET utf8mb4 
  COLLATE utf8mb4_general_ci;
