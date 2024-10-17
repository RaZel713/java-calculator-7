# 프리코스 1주차 미션 - 문자열 덧셈 계산기

---
우아한테크코스 7기 프리코스 1주차 미션, 문자열 덧셈 계산기를 구현한 저장소입니다.

## 기능 목록

### 입력: 사용자로부터 구분자와 양수로 구성된 문자열을 입력받기

- **입력형식**: `덧셈할 문자열을 입력해 주세요.`

### 로직 1: 입력받은 문자열의 유효성 검사하기

- **유효성 case 1**: `"//"`로 시작하는 문자열 일때
    - 문자열의 3번 인덱스 위치에 `'\'`, 4번 인덱스 위치에 `'n'`이 없는 경우 예외 처리한다.
    - 문자열의 2번 인덱스 위치에 숫자가 있는 경우 예외 처리한다.
    - 이때, 공백(`' '`) 또한 문자로 간주한다.

- **유효성 case 2**: `"//"`로 시작하지않는 문자열일 때
    - 문자열에 숫자와 기본구분자(쉼표(`','`)와 콜론(`':'`))를 제외한 다른 문자가 있으면 예외 처리한다.

### 로직 2: 입력받은 문자열에서 숫자를 분리하기

- 기본구분자는 쉼표(`','`)와 콜론(`':'`)이다.
- 커스텀 구분자는 문자열 앞부분의 `"//"`와 `"\n"` 사이에 위치하는 문자이다.
- 문자열 앞부분에 `"//"`가 없으면 기본 구분자만을 기준으로 문자열을 분리한다.
- 문자열 앞부분에 `"//"`가 있으면 기본 구분자와 커스텀 구분자로 문자열을 분리한다.
- 이때, `""`은 숫자 0으로 판단한다.

### 로직 3: 각 숫자의 합을 계산하기

### 출력: 덧셈의 결과를 출력하기

- **출력형식**: `결과 : (덧셈결과)`

## 예외 처리

- 사용자가 잘못된 값을 입력할 경우 `IllegalArgumentException` 을 발생시킨 후 애플리케이션은 종료

## 테스트 케이스

**case 1**:

**case 2**:

**case 3**:

