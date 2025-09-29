# Artnex MariaDB Schema

이 저장소에는 **퍼스널 컬러 & 브랜드 진단 서비스**용 MariaDB 스키마와 샘플 데이터가 포함되어 있습니다.

## Tables

### 1. style_toolkits (22 rows)
퍼스널 컬러/브랜드 스타일 아키타입 정의  
- 컬러 팔레트(HEX), 폰트, 소재/마감, 향·음악 키워드 포함  
- 총 22개 유형 (Cute, Romantic, Noble, Soft Modern, Clear Sporty … Formal)

### 2. question_bank (148 rows)
퍼스널 컬러 & 브랜드 진단 질문 데이터  
- 문항 ID (Q1~Q10, A-D 분기 포함)  
- 질문 텍스트 및 4개의 답변(각 답변은 색상 축 hue/value/chroma/contrast 변화량 포함)  
- 다음 질문 분기 로직 및 버전 관리  

## Usage
```bash
mysql -u root -p artnex < artnex.sql
