# 성격 유형 검사기

이 프로그램은 설문 조사 결과를 바탕으로 성격 유형을 계산하여 반환함 각 설문 항목과 선택지를 기반으로 점수를 계산한다

## 문제 아이디어

- **입력**:
  - `survey`: 각 설문 항목에 대한 두 가지 선택지를 나타내는 문자열 배열 예: `"RT"` (비동의는 `R`, 동의는 `T`).
  - `choices`: 사용자의 설문 응답을 나타내는 정수 배열. 1~7의 값으로 선택 정도를 나타냄
    - 1: 매우 비동의
    - 4: 중립
    - 7: 매우 동의

- **출력**:
  - 계산된 성격 유형을 나타내는 문자열 ( 예: `"RCJA"`)

---

## 알고리즘

1. **초기화**:
   - 각 성격 유형(`R, T, C, F, J, M, A, N`)에 대한 점수를 저장할 `Map`을 초기화한다
   - 모든 초기 점수는 `0`으로 설정

2. **점수 계산**:
   - 설문 항목과 사용자의 응답(`survey`, `choices`)을 순회하며 다음을 수행:
     - 설문 항목에서 비동의(`survey[i].charAt(0)`)와 동의(`survey[i].charAt(1)`) 성격 유형을 추출
     - 사용자의 선택지(`choices[i]`)에 따라 점수를 계산:
       - 1~3: 비동의 측에 점수 추가
       - 5~7: 동의 측에 점수 추가
       - 4: 중립(점수 변화 없음)

3. **성격 유형 결정**:
   - 각 성격 유형 쌍(`RT`, `CF`, `JM`, `AN`)에서 점수가 더 높은 유형을 선택
   - 점수가 같으면 사전순으로 앞에 오는 유형을 선택

4. **결과 반환**:
   - 계산된 성격 유형을 문자열로 반환
